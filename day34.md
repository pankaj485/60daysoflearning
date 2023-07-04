**# Day 34**

- [Section 9: Asynchronous JavaScript](#section-9-asynchronous-javascript)
  - [137. Section Overview](#137-section-overview)
  - [139. How JavaScript Works](#139-how-javascript-works)
  - [140. Promises](#140-promises)
    - [callbacks](#callbacks)
  - [141. ES8 - Async Await](#141-es8---async-await)
  - [142. ES9 (ES2018)](#142-es9-es2018)
    - [Object spread operator](#object-spread-operator)
  - [143. ES9(ES2018) - Async](#143-es9es2018---async)
    - [finally](#finally)
    - [for await of](#for-await-of)
  - [144. Job Queue](#144-job-queue)

# Section 9: Asynchronous JavaScript

## 137. Section Overview

Will learn:

- Web APIs
- Async/Await
- Callbacks
- Microtask Queue (Job Queue)
- Task Queue (Callback Queue)
- Promises
- Event loop

## 139. How JavaScript Works

A program has to:

1. Allocate memory
2. parse and execute the scripts(read and run commands)

A JavaScript engine consist of:

1. Memory Heap
2. Call Stack

Global variables are bad because they keep consuming the memory and access amount of global variables will cause memory related problems.

JavaScript has only one call stack which makes it single threaded. It makes it more simpler by avoiding complex implementations and preventing complex bugs like deadlocks.

By default, JavaScript is non-blocking which can makes it slower. With asynchronous JavaScript, it can be made non blocking.

Asynchronous processes happens while working with database, image processing, reading files and so on..

## 140. Promises

Are introduced in ES6.

Is an object which may produce a single value sometime in future. It can either be resolved, rejected or pending.

Promises are great for asynchronous programming.

example:

```jsx
const promise = new Promise((resolve, reject) => {
	if (true) {
		resolve("Promise is resolved");
	} else {
		reject("Promise is rejected");
	}
});

promise.then((result) => console.log(result)).catch((err) => console.log(err));
```

### callbacks

Are the functions which are triggered when a particular event occurs.

example: click event handler function when a button is clicked.

## 141. ES8 - Async Await

Is ES8 feature.

Under the hood, it returns the promise. It’s syntatic sugar to promises.

It makes asynchronous code synchronous and also simplifies the way to write the asynchronous functions.

while `.then()` and `.catch()` are used with promises, `try{}` and `catch(){}` are used with async awaits.

example:

```jsx
// example of working with APIs

// using promises
fetch("https://google.com")
	.then((resp) => resp.json())
	.then((data) => console.log(data))
	.catch((err) => console.log(err));

// using async functions
async function apiCall() {
	try {
		let resp = await fetch("https://google.com");
		let data = await resp.json();
		console.log(data);
	} catch (err) {
		console.log(err);
	}
}
```

## 142. ES9 (ES2018)

Features offered with ES9:

1. Object spread operator
2. finally
3. for await of

### Object spread operator

mdn reference: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Spread_syntax

example:

```jsx
// Object spread operator
const animals = {
	tiger: 23,
	lion: 5,
	monkey: 6,
};

const { tiger, ...otherAnimals } = animals;

console.log(tiger);
console.log(otherAnimals);
```

## 143. ES9(ES2018) - Async

### finally

will execute after running all the `.then()` and `.catch()` blocks.

It can be useful when a block of code can be implemented anyways no matter what.

mdn reference: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise/finally

example:

```jsx
function checkMail() {
	return new Promise((resolve, reject) => {
		if (Math.random() > 0.5) {
			resolve("Mail has arrived");
		} else {
			reject(new Error("Failed to arrive"));
		}
	});
}

checkMail()
	.then((mail) => {
		console.log(mail);
	})
	.catch((err) => {
		console.error(err);
	})
	.finally(() => {
		console.log("Experiment completed");
	});
```

### for await of

The for await...of statement creates a loop iterating over async iterable objects as well as sync iterables. This statement can only be used in contexts where await can be used, which includes inside an async function body and in a module.

mdn reference: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/for-await...of

example:

```jsx
const urls = [
	"https://google.com",
	"https://facebook.com",
	"https://instagram.com",
	"https://twitter.com",
];

const getData = async function () {
	const arrayOfPromises = urls.map((url) => fetch(url));
	for await (let request of arrayOfPromises) {
		const data = await request.json();
		console.log(data);
	}
};
```

## 144. Job Queue

Is came with ES6

Previously event loop had callback queue (task queue) before promises. In promises, we were able to handle the asynchronous code natively on JavaScript.

Job queue (micro-task queue) is introduced for the promises. It has higher priority when even loop will go through the queues as compared to callback queue.

Which means the event loop will first clear the Job queue then the callback queue.
