**# Day 35**

- [Section 9: Asynchronous JavaScript](#section-9-asynchronous-javascript)
  - [145. Parallel, Sequence and Race](#145-parallel-sequence-and-race)
  - [ES2020: allSettled()](#es2020-allsettled)
  - [ES2021: any()](#es2021-any)
  - [148. Threads, Concurrency and Parallelism](#148-threads-concurrency-and-parallelism)

# Section 9: Asynchronous JavaScript

## 145. Parallel, Sequence and Race

Promises can be run parallel, sequentially, raced based on need

parallel promises: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise/all

race promises: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise/race

example:

```jsx
// Generic function to trigger asynchronous operation
const promisify = (item, delay) => new Promise((resolve) => setTimeout(() => resolve(item), delay));

// Generic functions uing existing promisify method to trigger asynchronous task
const a = () => promisify("a", 100);
const b = () => promisify("b", 6000);
const c = () => promisify("c", 3000);

// parallel promises: runs all the promises parallelly together, waits for all to finish and returns after all of them are resolved
async function parallel() {
	const promises = [a(), b(), c()];
	const [output1, output2, output3] = await Promise.all(promises);
	return `Parallel promise is done: ${output1} ${output2} ${output3}`;
}

// race promises: returns whichever promise is solved at first and ignores other
async function race() {
	const promises = [a(), b(), c()];
	const output = await Promise.race(promises);
	return `Race promise is done: ${output}`;
}

// sequencial promises: runs all the promises one by one. Completes one first and then another
async function sequence() {
	const output1 = await a();
	const output2 = await b();
	const output3 = await c();

	return `Sequencial promise is done ${output1} ${output2} ${output3}`;
}

parallel().then(console.log);
race().then(console.log);
sequence().then(console.log);

// output:
// Race promise is done: a
// Parallel promise is done: a b c
// Sequencial promise is done a b c
```

## ES2020: allSettled()

mdn reference: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise/allSettled

Unlike `prmoise.all()` which short circuits the result and stop executing once any failure is discovered, the `promise.allSettled()` will execute all the provided promises even if they are failing. It will return the values until all the promises are returned.

example:

```jsx
// Generic function to trigger asynchronous operation
const promisify = (item, delay) => new Promise((resolve) => setTimeout(() => resolve(item), delay));

// Generic functions uing existing promisify method to trigger asynchronous task
const a = () => promisify("a", 100);
const b = () => promisify("b", 6000);
const c = () => promisify("c", 3000);

// allSettled: runs all the promises irrespective of status is resolved or rejected
async function allSettledPromises() {
	const promises = [a(), b(), c()];
	Promise.allSettled(promises)
		.then((data) => console.log(data))
		.catch((e) => console.log(e.message));
}

allSettledPromises();

// output:
// [
//   { status: 'fulfilled', value: 'a' },
//   { status: 'fulfilled', value: 'b' },
//   { status: 'fulfilled', value: 'c' }
// ]
```

## ES2021: any()

There is a new method added to promises in 2021! Unfortunately it isn't a very useful one, but I added here for you as an example that you can play around with using our previous example:

`Promise.any()` resolves if any of the supplied promises is resolved. Below we have 3 promises, which resolves at random times.

example:

```jsx
const p1 = new Promise((resolve, reject) => {
	setTimeout(() => resolve("A"), Math.floor(Math.random() * 1000));
});
const p2 = new Promise((resolve, reject) => {
	setTimeout(() => resolve("B"), Math.floor(Math.random() * 1000));
});
const p3 = new Promise((resolve, reject) => {
	setTimeout(() => resolve("C"), Math.floor(Math.random() * 1000));
});
```

Out of `p1`, `p2` and `p3`, whichever resolves first is taken by `Promise.any()`

```jsx
(async function () {
	const result = await Promise.any([p1, p2, p3]);
	console.log(result); // Prints "A", "B" or "C"
})();
```

What if none of the promises resolve? In that case `Promise.any()` throws an error!

## 148. Threads, Concurrency and Parallelism

With asynchronous JavaScript, the asynchronous task will not keep the main thread occupied since they are running on own worker threads in parallel. As soon as the asynchronous task is done, those worker threads will be killed.

The worker threads are managed and killed by JavaScript engine. The threads are called web workers. They are often running in the background and are managed by JavaScript engines.

The web workers don’t have access to all the features but has handy features like `setTimeOut()`

Same thing is followed by the Node.js also. It will run the worker threads on the background by itself whenever a new asynchronous task is to be handled like fetching data from APIs or reading the files.

Is bit more beyond the scope of the course. The topics can be self looked into.

1. Concurrency
2. Parallelism
3. Threads
4. Web workers
