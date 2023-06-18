**# Day 18**

- [Section 3: JavaScript Foundation II](#section-3-javascript-foundation-ii)
  - [33. Hoisting](#33-hoisting)
  - [37. Function Invocation](#37-function-invocation)
  - [38. function arguments](#38-function-arguments)
  - [39. Variable Environment](#39-variable-environment)

# Section 3: JavaScript Foundation II

## 33. Hoisting

Hoisting is a JavaScript mechanism where variables and function declarations are moved to the top of their scope before code execution.

variables are partially hoisted. (creates memory space for it but values are not assigned)

Note:

only `var` is hoisted but not `let` and `const`

only function declarations are hoisted but not function expressions

Hoisting allows to run functions above it’s creation phase.

It’s advised to not to keep the hoisting to prevent unpredictable behaviors by simply using `let` and `const` instead of `var`

## 37. Function Invocation

function declarations start with function keyword while function expression start with variable. Function declarations are hoisted while expressions are not.

Function Invocation is simply calling/execution of the function.

When a function is invoked, it will give:

1. execution context
2. arguments

## 38. function arguments

Are values being passed to the function when it’s invoked.

It’s only available inside of execution context of the function.

It looks like an array but isn’t array. No array methods can be used with it.

It’s advised to avoid arguments in the modern JavaScript and use spread operator instead.

`arguments` keyword is reserved in JavaScript and is accessible inside of each of the function execution contexts.

example:

```jsx
// using spread operator
function example(...args){
	console.log("arguments", arguments);
	console.log(Array.from(arguments));
	return `${args[0]} is first, ${args[1} is second.`
}

example("helo", "ke chaa");

```

## 39. Variable Environment

Is a space in execution context which means each function has own variable environment.

The variable inside of the variable environment of the function has nothing to do with the global variable.
If accessed variable is not available on the current variable environment then it will go to the outer scope and look for it by utilizing the scope chain.
