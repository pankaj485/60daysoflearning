**# Day 60**

- [Section 3: Protocols](#section-3-protocols)
  - [24. Websockets](#24-websockets)
    - [HTTP](#http)
    - [WebSockets Handshake](#websockets-handshake)
    - [Use cases of websockets](#use-cases-of-websockets)
    - [Pros of websocket](#pros-of-websocket)
    - [Cons of websocket](#cons-of-websocket)
    - [websocket implementation](#websocket-implementation)

# Section 3: Protocols

## 24. Websockets

Is bidirectional communication designed for web

Is built on top of HTTP

### HTTP

HTTP 1.0 opens and closes the connection each time request is made.

HTTP 1.1 keeps the connection persistent and makes the request and closes the connection when requests are done.

### WebSockets Handshake

Performs websocket handshake first before opening connection.

The connection is bidirectional unlike in HTTP where at a time either request or response only would be passed.

starts with `ws://` or `wss://`

example diagram:

![Untitled](https://github.com/pankaj485/60daysoflearning/assets/61234787/c3bf3f9a-d84b-477d-83a3-5c6b84a1c707)

websocket handshake process:

![Untitled](https://github.com/pankaj485/60daysoflearning/assets/61234787/03d03618-228e-48bd-be44-9375d39ca0df)

### Use cases of websockets

1. Real time chat applications
2. Live Feed
3. Multiplayer gaming
4. Showing client progress/logging

### Pros of websocket

1. Full duplex (no pulling) (mutltdirectional communication)
2. HTTP compatible
3. Firewall friendly (standard)

### Cons of websocket

1. Proxying is tricky (have to really understand how to terminate the websocket connection and read the message and create a new connection to send the disconnection message)
2. L7 LB challenging (timeouts)
3. Difficult to scale horizontally as it’s stateful

### websocket implementation

example code:

`server.js`

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
```

`client side`

```jsx
//client code
//let ws = new WebSocket("ws://localhost:8080");
//ws.onmessage = message => console.log(`Received: ${message.data}`);
//ws.send("Hello! I'm client")
```

`client side example`

All the clients are connected to a centralized server not to each other. The server first gets the message and then sends the message to the clients.

![Untitled](https://github.com/pankaj485/60daysoflearning/assets/61234787/f3659aab-210b-4980-80b8-0c22857bc12a)
