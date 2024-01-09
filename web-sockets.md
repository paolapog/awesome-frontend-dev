WebSockets is a communication protocol that provides full-duplex communication between a client and a server over a long-lived, persistent connection. This is different from the traditional HTTP protocol where the client has to initiate the request and the server responds to the request.

## How WebSockets Work:

1. **Establishing a Connection:** The WebSocket connection is established by upgrading from the HTTP protocol. The client sends a WebSocket handshake request, and the server sends a WebSocket handshake response, and then the data transfer can begin.

2. **Data Transfer:** Once the connection is established, data can be sent back and forth between the client and the server at any time, until the connection is closed. The data can be text or binary.

3. **Closing a Connection:** Either the client or the server can choose to send a close frame and close the WebSocket connection.

**Use Cases for WebSockets:**

1. **Real-Time Applications:** WebSockets are ideal for real-time applications where you need to show information to users as soon as it's available. Examples include chat applications, real-time gaming, live tracking systems, etc.

2. **Collaborative Editing:** WebSockets can be used for collaborative editing applications like Google Docs where multiple users can edit a document at the same time and see each other's changes in real-time.

3. **Streaming:** WebSockets can be used for streaming of data in applications like live video or audio broadcasting.

**Pros of WebSockets:**

1. **Full-Duplex Communication:** WebSockets provide a full-duplex communication channel. Once a WebSocket connection is established, it stays open until the client or server decides to close it. This allows for real-time data transfer.

2. **Efficiency:** WebSockets are more efficient than polling. With polling, the client has to ask the server for new data regularly, which can lead to a lot of unnecessary HTTP requests. With WebSockets, the server can send new data as soon as it's available.

3. **Reduced Latency:** Because there's no need to establish a new connection for every message, WebSockets can reduce the latency in your application.

**Cons of WebSockets:**

1. **Complexity:** WebSockets can be more complex to implement than traditional HTTP requests. There's also less tooling available for debugging WebSocket connections.

2. **Compatibility:** Not all web browsers support WebSockets. However, most modern browsers do.

3. **Security:** WebSockets can be vulnerable to attacks, such as Cross-Site WebSocket Hijacking (CSWSH). It's important to secure your WebSocket connections, for example by using the WebSocket Secure (WSS) protocol.

## Implementation 

Implementing a WebSocket in JavaScript involves creating a new WebSocket object, setting up event handlers for the connection, and sending/receiving data. Here's a basic example:

```javascript
// Create a new WebSocket.
var socket = new WebSocket('ws://your-websocket-url');

// Connection opened
socket.addEventListener('open', function (event) {
    socket.send('Hello Server!');
});

// Listen for messages
socket.addEventListener('message', function (event) {
    console.log('Message from server: ', event.data);
});

// Connection closed
socket.addEventListener('close', function (event) {
    console.log('Server closed connection: ', event);
});

// Connection error
socket.addEventListener('error', function (event) {
    console.log('Error: ', event);
});
```

In this example:

- A new WebSocket is created with the URL of the WebSocket server.
- An event listener is added for the 'open' event, which is fired when the connection is established. In this case, a message is sent to the server saying 'Hello Server!'.
- An event listener is added for the 'message' event, which is fired when a message is received from the server. The message data is logged to the console.
- Event listeners are also added for the 'close' and 'error' events, which are fired when the connection is closed or an error occurs.

Remember, If your server uses WebSocket Secure (WSS), the URL should start with `'wss://'` instead of `'ws://'`.