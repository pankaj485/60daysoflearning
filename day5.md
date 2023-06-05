**# Day 5**

- [39. Conceptual Asside: Arrays - Collections of Anything](#39-conceptual-asside-arrays---collections-of-anything)
- [40. Arguments and spread](#40-arguments-and-spread)
  - [arguments](#arguments)
  - [spread](#spread)
- [41. Framework Aside: Function Overloading](#41-framework-aside-function-overloading)
- [42. Conceptual Aside: Syntax Parsers](#42-conceptual-aside-syntax-parsers)

## 39. Conceptual Asside: Arrays - Collections of Anything

contains values separated by commas and can have different data types as it’s dynamically typed.

An array in JavaScript can have number, string, array, string, function, boolean, object and it’s still valid. It will hold collection of everything.

Is index based.

## 40. Arguments and spread

### arguments

holds the list of all the values of the all the parameters passed to the function.

while defining the functions, parameters are setup and while invoking the functions, the arguments are setup.

The memory space created for all the arguments while invoking it. If not passed then it’s undefined.

A default value can be passed to the function argument.

example:

```jsx
function sayHello(firstName, lastName, greeting = "hello") {
	console.log(greeting, firstName, lastName);
}
```

Inside the function scope, a special variable `arguments` can be accessed which holds information about the function argument. It’s like an array but isn’t exactly an array as it doesn’t contain enough array features. (indexing can be used)

### spread

Is a better way to use over arguments.

Is used with three dots `...`

The JavaScript spread operator (`...`) allows us to quickly copy all or part of an existing array or object into another array or object.

The spread operator is often used in combination with destructuring.

mozila docs on spread operator: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Spread_syntax

## 41. Framework Aside: Function Overloading

it’s the ability to create multiple functions of the same name with different implementations.

Is not directly available in the JavaScript as it’s dynamic and also arrays are object based.

## 42. Conceptual Aside: Syntax Parsers

Reads human written codes and evaluates what to execute and go through the standard rules character by character before it’s executed.

Syntax parser is part of JavaScript. It reads your code character by character, tells what your code does, and check if the grammar is correct or not. You can think syntax parser as an interpreter between your code and computer. It translates your code to machine readable code.
