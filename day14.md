**# Day 14**

- [Section 10: EXTRA: TypeScript, ES6, and Transpiled Languages](#section-10-extra-typescript-es6-and-transpiled-languages)
  - [82. Typescript, ES6, and Transpiled Languages](#82-typescript-es6-and-transpiled-languages)
    - [Transpile](#transpile)
- [Section 12: Extra: ES6 In-Depth](#section-12-extra-es6-in-depth)
  - [](#)
  - [87. Promises, Async, and Await](#87-promises-async-and-await)
    - [Promise](#promise)
    - [Async and Await](#async-and-await)

# Section 10: EXTRA: TypeScript, ES6, and Transpiled Languages

## 82. Typescript, ES6, and Transpiled Languages

### Transpile

Is process of converting syntax of one programming language to another. Examples: Typescript to JavaScript, Traceur (ES6 to standard ES5 JavaScript)

Typescript is transpiled into JavaScript. It’s not being run by any engine but instead compiled into JavaScript.

Typescript provides types to JavaScript which makes it less error prone.

# Section 12: Extra: ES6 In-Depth

##

## 87. Promises, Async, and Await

Functions in JavaScript are first class objects which means they can be assigned as a value and passed around.

Another important part of it is how JavaScript is executed. It relies on execution context and stacks. Each function will have own execution stack.

JavaScript is single threaded by nature but it uses concept of queue to handle multiple processes at a same time. The feature is not natively available with JavaScript but with extra third party engines.

### Promise

Is standardized approach to deal with asynchronous events and callbacks.

A promise object represents a future value for the process already running which will be eventually received but isn’t available right away.

Promise object is already present in JavaScript outside of the box.

Promise by itself doesn’t execute anything instead it will have function written inside of it which will be called can executed.

A promise can have 3 states:

1. Pending
2. Fulfilled
3. Rejected

For fulfilled and rejected states, there will be different functions.

more on promises: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise

### Async and Await

Are syntactic sugar to promises.

Provides more cleaner approach to write and debug the code.

Makes writing asynchronous process more simpler and standardized.

Any code that deals with async and await is under the hood dealing with promises also. Which means, the executed function code execution context is paused and main context is waiting.

Both can be used together but generally async and await is more cleaner.

more on async function: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/async_function
