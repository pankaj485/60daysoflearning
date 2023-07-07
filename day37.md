**# Day 37**

- [Section 11: Error Handling](#section-11-error-handling)
  - [157. Errors In JavaScript](#157-errors-in-javascript)
    - [Error constructor](#error-constructor)
    - [Built in error properties](#built-in-error-properties)
    - [Different types of error constructors in JavaScript](#different-types-of-error-constructors-in-javascript)
    - [How to handle errors?](#how-to-handle-errors)
  - [158. Try Catch](#158-try-catch)

# Section 11: Error Handling

## 157. Errors In JavaScript

### Error constructor

JavaScript has native `Error` constructor function and a new instance of error can be created using the constructor function.

A error object has to be thrown in order to stop the code execution (to act like an error)

Whenever a throw statement is encountered, the execution of the current function will stop and control will be passed to the next part of the call stack.

When the `throw` expression is encountered the current execution is stopped and will move to the next part of the call stack.

`throw` statements are used to raise exceptions.

### Built in error properties

The error object has following 3 built in properties:

1. name (name of the error)
2. message (error message)
3. stack (stack trace of the error. Shows where error happened.)

### Different types of error constructors in JavaScript

JavaScript has multiple built in error constructors.

1. Generic `Error` constructor
2. `SyntaxError` constructor
3. `ReferenceError` constructor

Any of the error will be thrown using the `throw` statement which will raise the exception and hence moves the current execution to the next part of call stack.

### How to handle errors?

In JavaScript, errors are handled with `catch()` method or `try{}` and `catch(){}` blocks.

If an error is raised then browser will throw it as: Runtime catch: onerror()

If an error is raised then browser will throw it as: process.on(’uncaughtException’)

If the error is not caught then it will be handled on runtime.

## 158. Try Catch

The try block is where the block of code is ran and `catch` block is where error is handled. If there will be any error or exceptions inside of the `try` block, it will move the flow to the `catch block` and will be handled there.

The `catch` block always excepts an error parameter.

Additionally we can also we the finally block which will be executing anyways after the respective blocks will be executed.

example:

```jsx
try {
	console.log("this runs when there's no exceptions");
} catch (error) {
	console.log("this runs when there are no exceptions");
} finally {
	console.log("this blocks runs after above blocks");
}
```
