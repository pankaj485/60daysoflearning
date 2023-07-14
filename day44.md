**# Day 44**

- [Section 2: Backend Communication Design Patterns](#section-2-backend-communication-design-patterns)
  - [7. Synchronous vs Asynchronous workloads](#7-synchronous-vs-asynchronous-workloads)
    - [Synchronous I/O](#synchronous-io)
    - [Asynchronous I/O](#asynchronous-io)
    - [Synchronous vs Asynchronous in Request Response](#synchronous-vs-asynchronous-in-request-response)
    - [Synchronous vs Asynchronous in real life](#synchronous-vs-asynchronous-in-real-life)
    - [Asynchronous workload is everywhere](#asynchronous-workload-is-everywhere)
    - [NodeJs example of synchronous and asynchronous workloads](#nodejs-example-of-synchronous-and-asynchronous-workloads)

# Section 2: Backend Communication Design Patterns

## 7. Synchronous vs Asynchronous workloads

Asynchronous simply means doing something while something else is still executing and wait for the result.

### Synchronous I/O

What happens with synchronous I/O

1. Caller sends a request and blocks.
2. Caller cannot execute any code meanwhile
3. Once the receiver will respond, the caller will unblock
4. Caller and Receiver are in sync

example of synchronous I/O:

1. Program asks OS to read from disk
2. Program main thread is taken off of the CPU
3. When reading is complete, program can resume execution

NodeJs explanation of synchronous implementation

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/72aa5cd4-9bb4-4db1-91d5-6ee8a2651bbe/Untitled.png)

### Asynchronous I/O

What happens with asynchronous I/O:

1. Caller sends a request
2. Caller can work until it gets a response
3. Caller either:
   1. Check if a response if ready (epoll, used by NodeJS)
   2. Receiver calls back when it’s done (io_uring)
4. Caller and Receiver are not necessarily in sync

example of an OS asynchronous call (NodeJS):

1. Program spins up a secondary thread.
2. Secondary thread reads from disk, OS blocks it.
3. Main program is still running and executing code.
4. Thread finish reading and calls back main thread.

NodeJS explanation

Following is bit older implementation as promises can be used easily now.

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/c963e47b-dc6f-48c6-a161-f2e5e3a4b174/Untitled.png)

### Synchronous vs Asynchronous in Request Response

- Synchronicity like is a client property.
- Most of the modern client libraries are asynchronous (example: async, axios).
- E.g: Clients send an HTTP request and do work

### Synchronous vs Asynchronous in real life

In synchronous communication, the caller waits for a response from receiver.

E.g: Asking some question in a meeting

In Asynchronous communication, the response can come whenever. Caller and receiver can do anything meanwhile.

E.g: Email

### Asynchronous workload is everywhere

1. Asynchronous Programming (promises/futures)
2. Asynchronous backend processing.
3. Asynchronous commits in postgres.
4. Asynchronous IO in Linux (epoll, io_uring)
5. Asynchronous replication
6. Asynchronous OS fsync (fs cache)

   Data doesn’t right away goes to the file system. It goes through caching and flushing

### NodeJs example of synchronous and asynchronous workloads

Reading a file `data.txt` in both synchronous and asynchronous way:

Asynchronous example:

```jsx
const fs = require("fs");

console.log("1");

fs.readFile("./data.txt", (error, response) => {
	console.log("file data: ", response.toString());
});

console.log("2");

// output:
// 1
// 2
// file data: hello there
```

Synchronous example:

```jsx
const fs = require("fs");

console.log("1");

const data = fs.readFileSync("./data.txt");
console.log("file data: ", data.toString());

console.log("2");

// output: (reading was scheduled)
// 1
// file data:  hello there
// 2
```
