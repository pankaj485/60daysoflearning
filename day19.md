**# Day 19**

- [Section 3: JavaScript Foundation II](#section-3-javascript-foundation-ii)
  - [40. Scope chain](#40-scope-chain)
  - [41. Scope](#41-scope)
  - [43. Function Scope vs Block Scope](#43-function-scope-vs-block-scope)
    - [Function Scope](#function-scope)
    - [Block Scope](#block-scope)
  - [45. Global Variables](#45-global-variables)
- [46. IIFE](#46-iife)

# Section 3: JavaScript Foundation II

## 40. Scope chain

Is a part of execution context.

Each context has a link to outside scope.

lexical scope is also called as static scope.

The scope chain will start from where variable is executed in the function to the global execution context.

Variable declared in a local scope is accessible to it’s own scope and the block below it while variable declared in global scope is accessible to all the part of the code.

## 41. Scope

Scope determines the accessibility of variables, objects, and functions from different parts of the code.

When a function is executed, an execution context is created which has own environment.

`[[scopes]]` is actually accessible property in global execution context out of the box which is window object.

## 43. Function Scope vs Block Scope

### Function Scope

JavaScript has function scope while most of other programming languages are having block scope.

With functional scope, we only create a new scope when there is a new function and the variables declared inside of the function will be accessible to it’s scope only.

### Block Scope

Block scope is the scope inside of the set of `{ }` which can be function or simple conditional statements like for loop or while loop. In JavaScript, `let` and `const` allows to use block scope.

## 45. Global Variables

Are variables defined inside of the global scope.

Too much of global variables causes memory leaks and variable collisions which can generate possible bugs.

Are advised to use as less as possible and rather use module bundlers and ES modules

# 46. IIFE

Immediately invoked function expression.

Is common JavaScript design pattern.

A anonymous function expression is executed immediately.

All the property created inside it are scoped to itself only but not on the global execution context.

A function expression is executed inside of an JavaScript expression.

example:

```jsx
// invoking expression which consist of function exrpession invocation
(function sayHello() {
	const greeting = "hello";
	console.log(greeting);
})();
```

It allows to attach private data to a function and create a fresh environment which won’t pollute the global execution context.
