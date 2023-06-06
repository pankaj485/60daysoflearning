**# Day 6**

- [43. Dangerous Aside: Automatic Semicolon Insertion](#43-dangerous-aside-automatic-semicolon-insertion)
- [44. Framework Aside: Whitespace](#44-framework-aside-whitespace)
- [45. Immediately Invoked Functions Expressions(IIFE)](#45-immediately-invoked-functions-expressionsiife)
- [46. Framework Aside: IIFE and Safe Code](#46-framework-aside-iife-and-safe-code)
- [47. Understanding Closures](#47-understanding-closures)
- [48. Understanding Closures](#48-understanding-closures)

## 43. Dangerous Aside: Automatic Semicolon Insertion

Semicolons are optional in core JavaScript.

Anywhere where syntax parser expects the semicolon would be, it will put one.

It’s always recommended to put the semicolon by self.

In case of return statements, the automatic semicolon insertion may cause unexpected errors.

example:

```jsx
// wrong way
function sayHello() {
	return;
	{
		greet: "hello";
	}
}

console.log(sayHello()); // may likely give undefined as the syntax parser will automatically put semicolon right after return and the code below it will be ignored.

// better way
function sayHello() {
	return { greet: "hello" };
}
```

## 44. Framework Aside: Whitespace

Is invisible character which creates literal space in the written code.

example: carriage returns, tabs, spaces

Makes the code more readable but is not executed while executing the code.

Extra white spaces are allowed in between variable declaration, object literals also the comments between them is allowed which is absolutely valid code.

It’s encouraged to have whitespaces in the code to make it more readable.

## 45. Immediately Invoked Functions Expressions(IIFE)

A function is special object which can be invoked (executed) on the fly (at the time of code execution)

IIFE is special function which can be invoked(executed) immediately after it’s creation.

example:

```jsx
let greeting = (function (name) {
	console.log("helloo", name);
})("John"); // involing the function immediately after creating it
```

All the required arguments are passed on the invoke expression itself. (inside of the parenthesis after declaration)

IIFE doesn’t require to have name as it will be immidiately invoked as the code is executed.

example:

```jsx
(function (name) {
	console.log("Hello", name);
})("Hari");

// output: Hello Hari
```

## 46. Framework Aside: IIFE and Safe Code

Is widely used in many frameworks and libraries.

Is written commonly before normal functions.

Has own execution context just like other functions.

IIFE can be invoked both outside and inside of the parenthesis.

example:

```jsx
// invoking outisde of parenthesis
(function (name) {
	console.log("Hello", name);
})("Hari");

// invoking inside of parenthesis
(function (name) {
	console.log("Hello", name);
})("Hari");
```

## 47. Understanding Closures

Allows functions to access the outer functions memory space from it’s inner scope.

A closure is the combination of a function bundled together (enclosed) with references to its surrounding state (the lexical environment).

In JavaScript, closures are created every time a function is created, at function creation time.

## 48. Understanding Closures

was more of code explaination so nothing more.

mdn example:

```jsx
function init() {
	var name = "Mozilla"; // name is a local variable created by init
	function displayName() {
		// displayName() is the inner function, that forms the closure
		console.log(name); // use variable declared in the parent function
	}
	displayName();
}
init();
```

Closure can have differnet behaviours based on the type of the variable used. i.e: `let` and `var`

reason:

Variables declared by `let` are only available inside the block where they’re defined.

Variables declared by `var` are available throughout the function in which they’re declared.

function scope vs block scope: https://medium.com/edge-coders/function-scopes-and-block-scopes-in-javascript-25bbd7f293d7
