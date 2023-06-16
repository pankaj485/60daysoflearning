**# Day 16**

- [Section 2: JavaScript Foundation](#section-2-javascript-foundation)
  - [14. Comparing Other Languages](#14-comparing-other-languages)
  - [15. Writing optimized code](#15-writing-optimized-code)
  - [16. Web Assembly](#16-web-assembly)
  - [17. Call Stack and Memory Heap](#17-call-stack-and-memory-heap)
  - [18. Garbage collection](#18-garbage-collection)
  - [Memory Leaks](#memory-leaks)
  - [Single Threaded](#single-threaded)
  - [JavaScript runtime](#javascript-runtime)

# Section 2: JavaScript Foundation

## 14. Comparing Other Languages

Mostly exe file are written in C++ and then compiled down to executable machine code.

Java uses JVM to compiles/interprets to byte code. It’s not native code. It requires another machine to read and execute.

JavaScript is interpreted and compiled both. Based on implementation, it can be both. Same with Python. It can be compiled too although, it’s fundamentally interpreted.

## 15. Writing optimized code

While writing JavaScript, Avoid using following things which slows down the execution.

1. eval()
2. arguments
3. for in
4. with
5. delete

The better ways are instead to use hidden classes and inline caching.

Inline cache will cache the repeated data and stores directly and use the execution instead of going through the same process each time.

Hidden class is used by compilers which means if multiple instances of a class is being created which will have same methods then it will consider to be efficient when the object declarations are done in the identical orders.

In general, the more predictable code for compiler, better it is.

## 16. Web Assembly

Is a concept which says why not use machine code directly instead of human code.

It enables us to skip the process of going through the interpretation and compilation an directly execute the code in the browser.

It’s still a futuristic vision.

## 17. Call Stack and Memory Heap

Memory allocation and all related process related to memory happens at memory heap.

Call stack ensures to keep track of what part of code is being executed.

Both are part of JavaScript runtime

It stores functions and variables as the code gets executed. Works on first in last out concept.

Simple variables can be used on the stack itself while complex data structure like objects and arrays are stored in memory heaps

stack overflow is a condition when the stack memory gets out of it’s capacity. Easiest way to do is when recursion happens or by any a call stack is filled.

## 18. Garbage collection

JavaScript is a garbage collected language. It frees unused memory by itself. But there's still some flaws to it. It uses mark and sweep algorithms to implement garbage collection.

## Memory Leaks

Reasons for memory leaks:

- using global variables
- event listeners
- setIntervals

## Single Threaded

It means only one instruction is running at a time.
Js has only 1 call stack which is why its single threaded. Its synchronous due to that.
There's combination of JavaScript engine, runtime, and event loop to execute js code in asynchronous nature.

## JavaScript runtime

It's combination of JavaScript engine, webapi, event loop, callback queue, call stack
webApi is not part of JavaScript but the feature is provided by browse. eg: setTimeout, DOM, fetch(), browsers uses external library to execute these while JavaScript runs under the hood.
The results received from webAPI is sored in the callback queue.
Call Stack is where the code execution is done.
The results received from callback queue will be sent to execute once the call stack is empty while running the JavaScript.
The event loop keeps monitoring the call stack and callback queue. Once all stack is empty it will move the execution from callback queue to the main thread (call stack)
