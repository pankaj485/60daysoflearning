**# Day 38**

- [159. Async error handling](#159-async-error-handling)
- [156. Async error handling 2](#156-async-error-handling-2)
- [157. Extending Errors](#157-extending-errors)

## 159. Async error handling

Try catch are compatible to handle the synchronous errors but not the asynchronous codes.

Handling async error can get quite confusing often.

To handle errors in promise, we use `.catch()` along with `.then()` blocks.

`.catch()` clause is always a must while working with promises.

example:

```jsx
Promise.resolve("async failure")
	.then((response) => {
		throw new Error("#1 fail");
		return response;
	})
	.then((response) => {
		console.log(resolve);
	})
	.catch((error) => {
		console.log(error);
	});
```

Multiple `.catch()` can be used on a promise chain.

For each promise, there should be `.catch()` attached.

## 156. Async error handling 2

Handing async await based asynchronous error is easier than handing promise based asynchronous error.

`try` and `catch()` blocks are used for async await just like in synchronous code.

It’s always advised to use `try` `catch()` blocks while using async await.

## 157. Extending Errors

`Error` is a constructor function. Utilizing the OOP concept, we can add more features to it.

We can customize the error messages and hide the information like error traces.

With this way, instead of printing the non required message to the user, which may lead to security vulnerabilities, we can generalize the message and only print the particular ones.

example:

```jsx
class DatabaseError extends Error {
	constructor(message) {
		super(message);
		this.name = "DB Error: ";
	}
}

class PermissionError extends Error {
	constructor(message) {
		super(message);
		this.name = "Permission Error: ";
	}
}

const dbError1 = new DatabaseError("Database error!!");
const permissionError1 = new PermissionError("Permission error!!");

console.log(dbError1.name, dbError1.message);
console.log(permissionError1.name, permissionError1.message);

// oputput
// DB Error:  Database error!!
// Permission Error:  Permission error!!
```

Handling error is really important part of the code. It allows to make sure that the code is not crashing and everything is under control.

Until there is handled error, things are fine.
