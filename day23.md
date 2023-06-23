**# Day 23**

- [Section 5: The 2 Pillars: Closures and Prototypal Inheritance](#section-5-the-2-pillars-closures-and-prototypal-inheritance)
  - [70. Functions are Objects](#70-functions-are-objects)
  - [71. First class citizens](#71-first-class-citizens)
  - [73. Higher Order Functions](#73-higher-order-functions)
  - [75. Closures](#75-closures)
  - [77. Closures and memory](#77-closures-and-memory)
  - [78. Closures and encapsulation](#78-closures-and-encapsulation)

# Section 5: The 2 Pillars: Closures and Prototypal Inheritance

## 70. Functions are Objects

Arrays and functions both are of objects types in JavaScript.

ways to invoke the function:

1. directly executing with parenthesis.
2. executing as an object property.
3. using `.call()` method.
4. using function constructor.

A function is an object with some special properties like `code()` `Name` and `properties` which are `call()` `applyl()` and `bind()`

## 71. First class citizens

In JavaScript, a function can be assigned to a variable, can be passed to another function as a parameter, can return a function as a return value of a function.

This property of functions being first class citizens allows JavaScript to enable functional programming.

example:

```jsx
// assigning function to to a variable
var sayHello1 = function () {
	console.log("sayHello1");
};

sayHello1(); // sayHello1

// passing function as a paramter
function sayHello2(paramFunction) {
	paramFunction();
}

sayHello2(function () {
	console.log("sayHello2");
});

// returning function as a value

function sayHello3() {
	return function () {
		console.log("sayHello3");
	};
}

sayHello3()(); // sayHello3
```

## 73. Higher Order Functions

Are functions which can take functions as an arguments or returns a function.

This property allows to make the code more flexible and allows to implement DRY practice.

example:

```jsx
const multiplyBy = (num1) => (num2) => console.log(num1 * num2);

const multiplyByTwo = multiplyBy(2)(3); // 6
const multiplyByEight = multiplyBy(2)(8); // 16
const multiplyByTen = multiplyBy(2)(10); // 20
```

## 75. Closures

Closure exists in JavaScript because of:

1. lexical scope
2. Functions being first class citizens

Closure is the combination of function and lexical environment from which it was declared.

It allows to access variable environment even after a function stack is popped.

In other words, a closure gives you access to an outer function's scope from an inner function. In JavaScript, closures are created every time a function is created, at function creation time

With the feature of the closure only, we can have functions as a first class citizens and lexical scoping(**where we write the function matters. Not where we call the function**).

The function parameters are treated just like variables and are stored locally. They are assigned the values which were passed as arguments when the function was called, elsewhere in the code.

MDN reference: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Closures

## 77. Closures and memory

Main benefits of closures:

1. Is memory efficient
2. Provides encapsulation

Was an really awesome example on memory to demonstrate the first point.

## 78. Closures and encapsulation

It allows to hide the unnecessary piece of information from the regular user.
