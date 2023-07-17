**# Day 45**

- [Section 2: Backend Communication Design Patterns](#section-2-backend-communication-design-patterns)
  - [11. Server Sent Events](#11-server-sent-events)
    - [What is server sent events?](#what-is-server-sent-events)
    - [server sent response architecture diagram](#server-sent-response-architecture-diagram)
    - [Pros of Server Sent Events Design pattern:](#pros-of-server-sent-events-design-pattern)
    - [Cons of Server Sent Events Design pattern:](#cons-of-server-sent-events-design-pattern)
    - [Demo on server sent events](#demo-on-server-sent-events)

# Section 2: Backend Communication Design Patterns

## 11. Server Sent Events

Is purely HTTP based

Will have one request but the response will be very very long. Once a request is made the response keeps on coming.

Server will keep on sending the responses and the client will parse the mini responses and utilize it on the go.

### What is server sent events?

1. A response has start and end
2. Client sends a request
3. Server sends logical events as part of response
4. Server never writes the end of the response
5. It is still a request but an unending response
6. Client parses the streams data looking forward
7. Works with request/response (HTTP)

### server sent response architecture diagram

Client sends the request, The server will respond with an event which is a bunch of bytes which client will understand and parse. The response is not technically finished. The server will send another pack of data and when it’s complete, client can close the connection.

![Untitled](https://github.com/pankaj485/60daysoflearning/assets/61234787/7ada71e1-ab00-4c13-b001-590de3882009)

### Pros of Server Sent Events Design pattern:

1. Is real time as the data is immediately fetched and fed.
2. Compatible with Request/Response (HTTP model)

### Cons of Server Sent Events Design pattern:

1. Client must be online (keep connect to server)
2. Client may not be able to handle and may disconnect (just like in short polling)
3. Polling is preferred for light clients
4. HTTP/1.1 problem (only upto 6 connections can be made on TCP connection on that domain. If all 6 connections are made for server sent requests then all the other connections will be blocked. In such case, HTTP2 can be used which allows almost 200 requests)

### Demo on server sent events

When a client requests to the server, It will keep sending the response in span of 1000ms until client will disconnect by itself.

`index.js`

```jsx
/* Client Code (in browser)

let sse = new EventSource("http://localhost:8080/stream");
sse.onmessage = console.log

*/

const app = require("express")();

app.get("/", (req, res) => res.send("hello!"));

app.get("/stream", (req, res) => {
	res.setHeader("Content-Type", "text/event-stream");
	send(res);
});
const port = process.env.PORT || 8888;

let i = 0;
function send(res) {
	res.write("data: " + `hello from server ---- [${i++}]\n\n`);

	setTimeout(() => send(res), 1000);
}

app.listen(port);
console.log(`Listening on ${port}`);
```

sample snapshot:

![Untitled](https://github.com/pankaj485/60daysoflearning/assets/61234787/76326504-ba21-40dd-87a5-11eb2f2cd876)
