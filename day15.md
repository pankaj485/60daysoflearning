**# Day 15**

- [Section 2: JavaScript Foundation](#section-2-javascript-foundation)
  - [6. Section Overview](#6-section-overview)
  - [7. JavaScript Engine](#7-javascript-engine)
  - [9. Inside the Engine](#9-inside-the-engine)
  - [11. Interpreters and Compilers](#11-interpreters-and-compilers)
    - [Interpreters](#interpreters)
    - [Compilers](#compilers)
    - [Interpreter vs compiler](#interpreter-vs-compiler)
  - [13. Inside the V8 engine](#13-inside-the-v8-engine)
    - [Just In Time Compilers (JIT)](#just-in-time-compilers-jit)

# Section 2: JavaScript Foundation

## 6. Section Overview

How browser works and how JavaScript works?

JavaScript Engine, JavaScript Runtime, Interpreter, Compiler, JIT Compiler, Call Stack, Heap, Memory,

## 7. JavaScript Engine

Computer doesn’t really know what JavaScript is.

JavaScript engine allows to convert the human written JavaScript code to computer readable code. Example: V8 engine.
The V8 engine is written with C++

The JavaScript engines follows the ECMA script standards. It standardize how the language should be like. As long as the standard is followed the engine is following the standards.

## 9. Inside the Engine

JavaScript engine is also just another program which will do the job of converting human readable JavaScript to machine readable code.

It gets the code and follows various standard process and produces machine readable code.

The engine majorly consist of:

1. Parser
2. AST (Abstract Syntax Tree)
3. Intrepreter
4. Profiler
5. Compiler

JavaScript is interpreted language due to which it’s synchronous in nature but V8 engine compiles the JavaScript to native machine code before executing. It increases the performance this way as compared to interpreting it.

## 11. Interpreters and Compilers

### Interpreters

Translates the code line by line on the fly.

JavaScript was traditionally was a compiled language.

### Compilers

Compiler works ahead of time unlike of interpreter and compiles down to the machine readable language.

It reads the whole code at once and figure out optimal way and create own program which is more optimized and the same code can be interpreted too. This is common in machine level codes.

Majority of languages go through the both the process in order to make the program optimal and faster.

Babel and Typescript are possibly the best examples of the compilers. Both are being heavily used in the JavaScript ecosystem.

Babel is a JavaScript compiler that takes your modern JS code and returns  browser compatible JS (older JS code).

Typescript is a superset of JavaScript that compiles down to JavaScript.

Both of these do exactly what compilers do: Take one language and convert into a different one!

### Interpreter vs compiler

Both have own pros and cons.

Interpreter are faster for single set of tasks but for repeated tasks, it will take longer time as compared to compilers.

Compiler will take some time to go through the code entirely, but it’s more smarter as it handles the recurring tasks smartly and doesn’t go through the same process like for interpreter.

## 13. Inside the V8 engine

A program may go through the both interpreter and compiler using Just In Time (JIT) compilers.

### Just In Time Compilers (JIT)

Is most optimal way to run JS

Initially code goes through interpreter which executes code line by line and generates bytecode. If any line of code is repeated then the profile(which detects such code) will then pass it to compiler and then optimize and pass it to compiler and then optimize and pass it to process. It keeps on going as long as code is running.

Interpreter allows to run code quickly while profiler with compiler will optimize the code as we are running the code on the other side.

JavaScript is both Interpreted and compiled language as it uses JIT compilers. It’s based on the technical implementation.
