## Code Appendix: File Upload Communication

This appendix provides an overview of the file upload mechanism between the companion application and the hardware peripheral. Both the implementation details for the client-side ( Written in TypeScript) and the server-side (C for ESP32) are included.

### Uploading a File

#### Function Signature

```typescript
async uploadFile(serverIP: string, serverPort: number = 5000): Promise<{ status: FILE_ERROR, filename: string }>
```

#### Parameters

- `serverIP`: The IP address of the hardware peripheral.
- `serverPort`: The port at which the TCP socket is listening for connections (default is 5000).

#### Return Values

- `status`: A `FILE_ERROR` enum indicating whether the file upload was successful.
- `filename`: The name of the file as stored on the hardware peripheral.

### Client-Side Implementation (Companion Application)

```typescript
async uploadFile(serverIP: string, serverPort: number = 5000): Promise<{ status: FILE_ERROR, filename: string }> {
    console.log(`Attempting to upload document to ESP32 at ${serverIP}:${serverPort}`);
    
    if (!this.binaryData) {
        console.error("No binary data available");
        return { status: FILE_ERROR.FILE_UPLOAD_FAILED, filename: "" };
    }
    
    return new Promise((resolve, reject) => {
        const client = TcpSocket.createConnection({ host: serverIP, port: serverPort, tls: false }, () => {
            console.log('Connected to ESP32 server');
            
            let fname = this.filename_.length >= 10 ? this.filename_.substring(0, 10) + "." + this.extension : this.filename_;
            console.log("Attempting to write filename:", fname);
            client.write(fname);
            
            client.on('data', (data) => {
                const response = data.toString('utf8');
                console.log('Response from server:', response);
                
                if (response.includes('Filename received successfully')) {
                    console.log('Sending write command to ESP32');
                    client.write('write');
                } else if (response === 'OK') {
                    console.log('Sending file data:', this.binaryData);
                    const fileBuffer = Buffer.from(this.binaryData);
                    client.write(fileBuffer);
                } else if (response === 'UPLOAD_COMPLETE') {
                    client.end();
                    resolve({ status: FILE_ERROR.FILE_SUCCESS, filename: this.filename_ });
                } else {
                    console.error('Unexpected server response:', response);
                    client.destroy();
                    reject({ status: FILE_ERROR.FILE_UPLOAD_FAILED, filename: "" });
                }
            });
        });
        
        setTimeout(() => {
            if (!client.destroyed) {
                console.error('Upload timed out');
                client.destroy();
                reject({ status: FILE_ERROR.FILE_UPLOAD_FAILED, filename: "" });
            }
        }, 30000);
        
        client.on('error', (error) => {
            console.error('TCP socket error:', error);
            reject({ status: FILE_ERROR.FILE_UPLOAD_FAILED, filename: "" });
        });
        
        client.on('close', (hasError) => {
            if (hasError) {
                console.error('Connection closed with error');
                reject({ status: FILE_ERROR.FILE_UPLOAD_FAILED, filename: "" });
            }
        });
    });
}
```

### Server-Side Implementation (ESP32 Hardware Peripheral)

```c
static void tcp_server_write(void *pvParameters) {
    TaskParams *params = (TaskParams *)pvParameters;
    int client_socket = params->client_socket;
    char *filepath = params->filepath;
    char response[256];
    FILE *file = fopen(filepath, "wb");
    
    if (!file) {
        ESP_LOGE(TAG, "Failed to open file: %s", filepath);
        sprintf(response, "File: %s not found", filepath);
        send(client_socket, response, strlen(response), 0);
    } else {
        sprintf(response, "OK");
        send(client_socket, response, strlen(response), 0);
        
        while (1) {
            int len = recv(client_socket, read_buffer, BUFFER_SIZE, 0);
            if (len < 0) {
                if (errno == EWOULDBLOCK || errno == EAGAIN) {
                    ESP_LOGW(TAG, "Receive timeout");
                    break;
                } else {
                    ESP_LOGE(TAG, "Receive failed: errno %d", errno);
                }
            } else if (len == 0) {
                ESP_LOGI(TAG, "Client disconnected");
                break;
            } else {
                fwrite(read_buffer, 1, len, file);
                fflush(file);
            }
        }
    }
    
    fclose(file);
    close(client_socket);
    free(params);
    vTaskDelete(NULL);
}
```

