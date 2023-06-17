**# Day 17**

- [Section 3: JavaScript Foundation II](#section-3-javascript-foundation-ii)
  - [31. Execution Context](#31-execution-context)
  - [32. Lexical Environment](#32-lexical-environment)

# Section 3: JavaScript Foundation II

## 31. Execution Context

Each function has own execution context.

Initially a global execution context is created when program is started to get executed. Other execution contexts are created above it.

The global execution context has 2 major things (even for an empty file):

1. Global object
2. this

## 32. Lexical Environment

Is where you write something.

Each execution context has own lexical environment which means each function has own lexical environment.

In JavaScript, lexical scope(available data + variables where the function was defined) determines our available variable. Not where the function is called(dynamic scope).

The very first lexical environment is global lexical environment.
