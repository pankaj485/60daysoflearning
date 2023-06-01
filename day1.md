**# Day 1**

- [10. The Global Environment and the global object](#10-the-global-environment-and-the-global-object)
- [11. The execution context - Creation and Hoisting](#11-the-execution-context---creation-and-hoisting)
  - [Hoisting](#hoisting)
- [12. Conceptual Aside: JavaScript and undefined](#12-conceptual-aside-javascript-and-undefined)
- [13. The execution context - Code Execution](#13-the-execution-context---code-execution)
- [14. Conceptual Aside: Single Threaded, Synchronous Execution:](#14-conceptual-aside-single-threaded-synchronous-execution)
  - [Single threaded](#single-threaded)
  - [synchronous](#synchronous)
- [15. Function Invocation and the Execution Stack](#15-function-invocation-and-the-execution-stack)
  - [Invocation](#invocation)
  - [Execution Stack](#execution-stack)
- [16. Functions, Context and Variable Environments](#16-functions-context-and-variable-environments)
  - [Variable Environments](#variable-environments)
- [17. The Scope Chain](#17-the-scope-chain)

## 10. The Global Environment and the global object

Js code runs inside of an execution context.

There could be more than 1 execution context while running the code.

The base execution context is the global execution context.

What is global: which is accessible anywhere in the codebase. It creates:

1. global object
2. special variable called this

Even if the js file is empty, the file will executed and an execution context is created which will create global object and `this` variable.

The global object for the browsers is window object which. At the global level `this` and `window` is same.

Variables that are not inside of any function can be considered as global.

only `var` is part of the global execution window. `let` and `const` can’t be accessed in window object.

## 11. The execution context - Creation and Hoisting

### Hoisting

It is the default behavior of moving all the declarations at the top of the scope before code execution.

Which allows to access the variables and functions before it’s declaration. (in a limited way)

variable and functions in JavaScript are hoisted.

Execution context is responsible or this behavior.

In the execution context creation phase, as the parser run through the code, it recognizes where function and variables are created and sets up the memory space for the variables and functions before executing the code line by line.

In case of the variable, it doesn’t put the declarations but simply puts the placeholder `undefined` . All variables are set to `undefined` initially in Js.

## 12. Conceptual Aside: JavaScript and undefined

`not defined` and `undefined` isn’t same in Js.

`undefined` is special value is JavaScript which means the value is not set for the variable but variable is declared.

`not defined` is when one tries to access a variable which is not declared.

note: don’t set the values to undefined. It generally means that programmer haven’t set the value and the variables which is being accessed doesn’t have any values.

## 13. The execution context - Code Execution

The execution context has 2 phases:

1. creation phase: sets up variables and functions in the memory
2. execution phase: executes the code line by line

## 14. Conceptual Aside: Single Threaded, Synchronous Execution:

### Single threaded

Means one command is executed at a time.

JavaScript behaves in single threaded manner.

### synchronous

Means one line at a time in the order that appears.

## 15. Function Invocation and the Execution Stack

### Invocation

Means to run or call the function.

In JavaScript it’s done by using parenthesis after function name.

### Execution Stack

Is the stack of execution contexts.

How it occurs: when one function is called inside of other function, a new execution context is created and is kept on top of the current execution context.

Every function creates it’s own execution context while running.

## 16. Functions, Context and Variable Environments

### Variable Environments

Is related to where the variables live and how they are related to each other in the memory.

For example, each variable has it’s own execution context which has own variable environments.

Even if variable names are same inside of multiple functions, the variable has own environment which is scoped to the function it was created with.

## 17. The Scope Chain

If current function execution context is not having the request variable then it will look for it’s outer environment. The outer environment depends on how the function is kept lexically. Which often times is global execution context. Which means the functions execution scope is inside of the global execution context.

The chain of looking for the variable in the outer environment is called the scope chain.

Which means if a function is written inside of a function then it’s outer scope chain will be `current scope → the scope of the function inside of which it was written → global execution context` (as the parent function was written in the global context)
