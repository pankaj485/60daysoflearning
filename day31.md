**# Day 31**

- [Section 7: Functional Programming](#section-7-functional-programming)
  - [123. Higher Order Functions and Closures](#123-higher-order-functions-and-closures)
    - [Higher order functions](#higher-order-functions)
    - [Closures](#closures)
  - [124. Currying](#124-currying)

# Section 7: Functional Programming

## 123. Higher Order Functions and Closures

### Higher order functions

A function which takes one or more functions as arguments or returns functions as a result.

### Closures

Are mechanism for containing some sort of state.

Is ability of a function to access the items outside of it’s block scope even after outer function is executed.

Allows to create the data privacy.

## 124. Currying

Currying is a technique where a function with multiple arguments is transformed into a sequence of functions, each taking a single argument.

In other terms, currying is when a instead of taking all arguments at one takes the first one and returns a new function, which takes the second one and returns a new function, which takes the third one, etc. until all arguments are completed.

It allows to create utility functions which can save memories and more simpler.

example:

```jsx
// A curried function that takes a number 'a' and returns another function that multiplies any number 'b' by 'a'.
const curriedMutiply = (a) => (b) => a * b;

// executing the curried function
console.log(curriedMutiply(5)(3)); // 15
```
