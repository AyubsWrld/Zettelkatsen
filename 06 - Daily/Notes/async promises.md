#### Abstract 

```typescript
async function_( arg : type ) : Promise<{ return : type  , return : type }> {

	return new Promise( ( resolve , reject ) =>{
		resolve( { return , return } )	
	}) ; 
}
```

#### Practical Application  
___
```typescript 
  async uploadFile(serverIP: string, serverPort: number = 5000): Promise<{status: FILE_ERROR, filename: string}> {
      console.log(`Attempting to upload document to ESP32 at ${serverIP}:${serverPort}`);

      if (!this.binaryData) {
          console.error("No binary data available");
          return {status: FILE_ERROR.FILE_UPLOAD_FAILED, filename: ""};
      }

      return new Promise((resolve, reject) => {
          const client = TcpSocket.createConnection({
              host: serverIP,
              port: serverPort,
              tls: false
          }, () => {
              console.log('Connected to ESP32 server');
              
	  
	      var fname ; 
	      if( this.filename_.length >= 10 ){ fname = this.filename_.substring(0 , 10) + "." + this.extension ; }else{fname = this.fileName} 
	      console.log("Attempting to write filenmae : " , fname ) ; 
	      console.log("Spliced : " , this.filename_.substring( 0 , 10 )); 
	      console.log("Length : " , this.filename_.length) ; 
              client.write( fname );
              
              // Set up data handler for all responses
              client.on('data', (data) => {
                  const response = data.toString('utf8');
                  console.log('Response from server:', response);
                  
                  if (response.includes('Filename received successfully')) {
                      console.log('Sending write command to ESP32');
                      client.write('write');
                  } 
                  else if (response === 'OK') {
                      // Send the actual file data throws here 
                      console.log('Sending file data: ' , this.binaryData);
		      console.log("Socket status: " , client.destroyed);
                      const fileBuffer = Buffer.from(this.binaryData);
                      client.write(fileBuffer);
                      
                      // Don't end the connection yet - wait for upload confirmation
                      // We'll add a timeout instead
                  } 
                  else if (response === 'UPLOAD_COMPLETE') {
                      // Only close the connection after success confirmation
                      client.end();
                      resolve({status: FILE_ERROR.FILE_SUCCESS, filename: this.filename_});
                  }
                  else {
                      console.error('Unexpected server response:', response);
                      client.destroy();
                      reject({status: FILE_ERROR.FILE_UPLOAD_FAILED, filename: ""});
                  }
              });
          });

          setTimeout(() => {
              if (client.destroyed === false) {
                  console.error('Upload timed out');
                  client.destroy();
                  reject({status: FILE_ERROR.FILE_UPLOAD_FAILED, filename: ""});
              }
          }, 30000); 

          client.on('error', (error) => {
              console.error('TCP socket error:', error);
              reject({status: FILE_ERROR.FILE_UPLOAD_FAILED, filename: ""});
          });
          
          client.on('close', (hasError) => {
              if (hasError) {
                  console.error('Connection closed with error');
                  reject({status: FILE_ERROR.FILE_UPLOAD_FAILED, filename: ""});
              }
          });
      });
  }

```

___

Tags : #programming #patterns #typescript