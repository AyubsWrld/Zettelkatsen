The `Server` class in the `socket.io` library is a key part of setting up a WebSocket server to enable real-time, bidirectional communication between a server and its clients. This class manages the entire WebSocket connection process, handles various client events, and allows for easy broadcasting of messages.

Here’s a breakdown of how the `Server` class and the provided code work:

### 1. **Instantiating the Server**
```javascript
import { Server } from 'socket.io';

const io = new Server({
  cors: {
    origin: ['http://localhost:8081']
  }
});
```
- The `Server` class is instantiated with configuration options. In this case, the `cors` option specifies that only requests from `http://localhost:8081` are allowed.
- **CORS (Cross-Origin Resource Sharing)**: Since WebSockets are subject to the same-origin policy, the `cors` option enables the server to accept connections from different origins for development purposes.

### 2. **Listening for Connections**
```javascript
io.on('connection', (socket) => {
  console.log(`Connected: ${socket.id}`);
```
- The `io.on('connection')` event is triggered each time a new client connects to the server. 
- `socket` is an object that represents the connection between the server and a specific client, uniquely identified by `socket.id`.
- **Example**: When a client connects, it logs the connection with `console.log(`Connected: ${socket.id}`);`.

### 3. **Listening for Client Messages**
```javascript
socket.on('clientMessage', (message) => {
  console.log(`Message from client: ${message}`);
  // Send a response back to the client
  socket.emit('serverMessage', `Server received: ${message}`);
});
```
- `socket.on('clientMessage')` listens for a custom event called `clientMessage` from the client. The client can emit this event to send messages to the server.
- When a `clientMessage` is received, the server logs it and then responds by emitting a `serverMessage` event back to the client using `socket.emit`.
- This enables a back-and-forth conversation between the client and server.

### 4. **Handling Disconnection**
```javascript
socket.on('disconnect', () => {
  console.log(`Disconnected: ${socket.id}`);
});
```
- `socket.on('disconnect')` is a built-in event triggered when a client disconnects from the server (e.g., when they close their browser).
- This lets the server know when a specific client has left, so it can manage resources or notify other users if needed.

### 5. **Starting the Server**
```javascript
io.listen(3000);
```
- `io.listen(3000);` starts the WebSocket server on port `3000`. This port is where the server listens for incoming WebSocket connections from clients.

### Summary
In essence, the `Server` class:
- Sets up a WebSocket server that listens for client connections.
- Enables custom events (e.g., `clientMessage` and `serverMessage`) for real-time communication.
- Manages connections and disconnections for each client uniquely by `socket.id`.
- Is highly flexible, allowing for CORS setup, broadcasting events to specific clients, groups of clients, or all clients at once.

This setup enables the server to handle real-time interactions efficiently, such as in chat applications, multiplayer games, live updates, and more.

___

Tags : #programming #socketio #Networking 