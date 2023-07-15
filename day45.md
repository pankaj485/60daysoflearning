**# Day 45**

- [Section 2: Backend Communication Design Patterns](#section-2-backend-communication-design-patterns)
  - [Push](#push)
    - [What is push?](#what-is-push)
    - [Pros of Push Pattern](#pros-of-push-pattern)
    - [Cons of Push Pattern](#cons-of-push-pattern)
    - [Example of push pattern](#example-of-push-pattern)

# Section 2: Backend Communication Design Patterns

## Push

Is one of the famous pattern if one needs the response faster.

Request response is always an ideal pattern for all the workloads.

If client needs real time notification from backend, push pattern can be useful.

Push case is basically forcing a request.

### What is push?

Push pattern works in following way:

1. Client connects to server (bidirectional connection)
2. Server sends data to the client.
3. Client doesn’t have to request anything.

Protocol must be bidirectional (TCP can also work though)

The push model is used by `RabbitMQ`. It is an open-source message-broker software that originally implemented the Advanced Message Queuing Protocol and has since been extended with a plug-in architecture to support Streaming Text Oriented Messaging Protocol, MQ Telemetry Transport, and other protocols.

working of the push model: once bidirectional connection is setup, the backend gets and sends message to the client.

![Untitled](https://github.com/pankaj485/csv-parser/assets/61234787/6e15bb64-f085-40ee-8156-0d634dccb517)

### Pros of Push Pattern

1. Is real time
2.

### Cons of Push Pattern

1. Client must be online (connected to server) to receive the responses.
2. Clients might not be able to handle the load coming up from the server.
3. Requires a bidirectional protocol
4. Polling is only preferred for light clients

### Example of push pattern

Creating a simple websocket server

`index.js`

```jsx
const http = require("http");
const WebSocketServer = require("websocket").server;
let connections = [];

//create a raw http server (this will help us create the TCP which will then pass to the websocket to do the job)
const httpserver = http.createServer();

//pass the httpserver object to the WebSocketServer library to do all the job, this class will override the req/res
const websocket = new WebSocketServer({ httpServer: httpserver });
//listen on the TCP socket
httpserver.listen(8080, () => console.log("My server is listening on port 8080"));

//when a legit websocket request comes listen to it and get the connection .. once you get a connection thats it!
websocket.on("request", (request) => {
	const connection = request.accept(null, request.origin);
	connection.on("message", (message) => {
		//someone just sent a message tell everybody
		connections.forEach((c) =>
			c.send(`User${connection.socket.remotePort} says: ${message.utf8Data}`)
		);
	});

	connections.push(connection);
	//someone just connected, tell everybody
	connections.forEach((c) => c.send(`User${connection.socket.remotePort} just connected.`));
});

//client code
//let ws = new WebSocket("ws://localhost:8080");
//ws.onmessage = message => console.log(`Received: ${message.data}`);
//ws.send("Hello! I'm client")
```

Usage:

![Untitled](https://github.com/pankaj485/csv-parser/assets/61234787/b68c2a55-7ae6-4866-a01f-76fdf82e329e)
