**# Day 46**

- [Section 2: Backend Communication Design Patterns](#section-2-backend-communication-design-patterns)
  - [9. Polling](#9-polling)
    - [When is polling used?](#when-is-polling-used)
    - [Short pulling](#short-pulling)
    - [short polling architecture diagram](#short-polling-architecture-diagram)
    - [How short pulling works?](#how-short-pulling-works)
    - [Pros of short pulling](#pros-of-short-pulling)
    - [Cons of short pulling](#cons-of-short-pulling)
    - [Demo application with short pulling.](#demo-application-with-short-pulling)
  - [10. Long Pulling](#10-long-pulling)
    - [When is long polling used?](#when-is-long-polling-used)
    - [long polling architecture diagram](#long-polling-architecture-diagram)
    - [How long pulling works?](#how-long-pulling-works)
    - [Long polling advantages](#long-polling-advantages)
    - [Long polling disadvantages](#long-polling-disadvantages)
    - [Demo application with long pulling.](#demo-application-with-long-pulling)

# Section 2: Backend Communication Design Patterns

## 9. Polling

Is very common, popular and easy to implement design pattern.

Is a good communication style.

### When is polling used?

1. Where request/response time is not ideal and takes a long time to execute.

   example: Uploading a YouTube video.

2. The back end wants to sends notification.
   - A user just logged in

### Short pulling

Is very common when a request takes long time to complete and you want to execute it asynchronously on background.

A large request is broken down into multiple simpler smaller request and responses.

Can be useful to check if a certain request which ideally will be taking larger time is completed or not and then deliver the response to the client once it receives indication of completion.

### short polling architecture diagram

working of short polling:

client keeps requesting for completion of the request. For each request made for the confirmation a request id is sent to client and when request is completed and response can be sent, server will send response instead of request id

![Untitled](https://github.com/pankaj485/60daysoflearning/assets/61234787/a9c59870-15c1-459b-99af-52d96096daae)

### How short pulling works?

1. Client sends a request
2. Server responds immediately with a handle
3. The request is not immediately completed but later executes the request and later continuously check the result.
4. The client uses that handle to check for the status.

### Pros of short pulling

1. Is simple to implement.
2. Is good for long running requests.
3. Client can disconnect the moment it wants to.

### Cons of short pulling

1. Is too chatty (multiple requests has to be made each instance of time for each client. )
2. Due to frequent requests (which is configurable), It fills network bandwidth and may spike up the bills.
3. Wasted backend resources (just to check the completion, it has to perform operation which is majority of time not serving actual data response)

### Demo application with short pulling.

Checking if a job is done with progress with a simple NodeJS application.

When a POST request is made, it will respond back with the `JobId`. The request completion will progress by 10% every 3000ms. Until it’s 100%, it will give the current progress and when it’s 100%, it will response back with the completion message (response data).

When a GET request is made with the `JobId` as a parameter, it will print the current progress of the `POST` request.

`index.js`

```jsx
const app = require("express")();
const jobs = {};

app.post("/submit", (req, res) => {
	const jobId = `job:${Date.now()}`;
	jobs[jobId] = 0;
	updateJob(jobId, 0);
	res.end("\n\n" + jobId + "\n\n");
});

app.get("/checkstatus", (req, res) => {
	console.log(jobs[req.query.jobId]);
	res.end("\n\nJobStatus: " + jobs[req.query.jobId] + "%\n\n");
});

app.listen(8080, () => console.log("listening on 8080"));

function updateJob(jobId, prg) {
	jobs[jobId] = prg;
	console.log(`updated ${jobId} to ${prg}`);
	if (prg == 100) return;
	this.setTimeout(() => updateJob(jobId, prg + 10), 3000);
}
```

Making a POST request to `http://localhost:8080` with CURL

```jsx
curl -X POST http://localhost:8080/subimt
```

Checking the status of the request by providing jobId as a query param:

```jsx
curl http://localhost:8080/checkstatus?jobId=job:<jobId>
```

![Untitled](https://github.com/pankaj485/60daysoflearning/assets/61234787/a3882f88-8555-4bc8-bb51-40d367a2cb21)

## 10. Long Pulling

Is used to avoid chatty behavior of short pulling.

Generally means talk to be only when the response ready. Server will response back on the request only if the request is ready to send back.

Technically client keeps waiting until the subscribed message isn’t received.

Although pulling is to wait for the right response, there can be variation of timeouts also.

The long polling model Is used by kafka.

### When is long polling used?

1. When a request takes long time to process like uploading a Youtube video.
2. The back end want to send notifications (a user just logged in)

### long polling architecture diagram

working of long polling:

Is is relatively a longer request as client has to wait for a certain time to get the response but the advantage over normal request response is that it can be disconnected.

![Untitled](https://github.com/pankaj485/60daysoflearning/assets/61234787/8adcf148-81cc-4bd1-a033-ce14e0d96810)

### How long pulling works?

1. Client sends request.
2. Server responds immediately with a handle.
3. Server continues to process the request.
4. Client uses that handle to check for status.
5. Server doesn’t reply until it has the response. It allows to make the pulling less chatty and hence reduces the network traffic.

### Long polling advantages

1. Is less chatty and is more backend friendly as as relatively less request is required for the same resource.
2. Unlike normal request/response pattern, client can disconnect the request.

### Long polling disadvantages

1. Not real time (It is real time only at the moment we get response)

### Demo application with long pulling.

Check if a job is done with progress with a simple NodeJS application.

When a POST request is made, it will respond back with the `JobId`. The request completion will progress by 10% every 3000ms. When it’s 100%, it will response back with the completion message (response data).

When a GET request is made with the `JobId` as a parameter, it will keep waiting until the progress is 100% and server response back.

`index.js`

```jsx
const app = require("express")();
const jobs = {};

app.post("/submit", (req, res) => {
	const jobId = `job:${Date.now()}`;
	jobs[jobId] = 0;
	updateJob(jobId, 0);
	res.end("\n\n" + jobId + "\n\n");
});

app.get("/checkstatus", async (req, res) => {
	console.log(jobs[req.query.jobId]);
	//long polling, don't respond until done
	while ((await checkJobComplete(req.query.jobId)) == false);
	res.end("\n\nJobStatus: Complete " + jobs[req.query.jobId] + "%\n\n");
});

app.listen(8080, () => console.log("listening on 8080"));

async function checkJobComplete(jobId) {
	return new Promise((resolve, reject) => {
		if (jobs[jobId] < 100) this.setTimeout(() => resolve(false), 1000);
		else resolve(true);
	});
}

function updateJob(jobId, prg) {
	jobs[jobId] = prg;
	console.log(`updated ${jobId} to ${prg}`);
	if (prg == 100) return;
	this.setTimeout(() => updateJob(jobId, prg + 10), 10000);
}
```
