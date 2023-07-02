**# Day 32**

- [Section 7: Functional Programming](#section-7-functional-programming)
  - [125. Partial Application](#125-partial-application)
  - [127. Memoization 1](#127-memoization-1)
  - [128. Memoization 2](#128-memoization-2)
  - [129. Compose and Pipe](#129-compose-and-pipe)
    - [Compose](#compose)
    - [Pipe](#pipe)
  - [130. Arity](#130-arity)
  - [131. The Answer to everything](#131-the-answer-to-everything)

# Section 7: Functional Programming

## 125. Partial Application

Is a way to partially apply a function.
While in currying, it will accept the arguments one by one, in partial application, it will accept the rest of the arguments in the second phase.

example:

```jsx
const multiply = (a) => (b, c) => a * b * c;
console.log(multiply(5)(2, 3));
```

## 127. Memoization 1

Caching is way to store values to use it for later for faster implementation.

Memoization is a type of caching.

example:

```jsx
// generic way to execute
function addTo80(n) {
	console.log("long time");
	return n + 80;
}

// creating data for memoization cache
let cache = {};

function memoizedAddTo80(n) {
	// if data is present in cache, then return it from cache
	if (n in cache) {
		console.log("getting from cache");
		return cache[n];
	} else {
		// if data no present in cache, then add result to cache and return it from cache
		console.log("taking longer route");
		cache[n] = n + 80;
		return cache[n];
	}
}

console.log(memoizedAddTo80(5)); // executes without cache
console.log(memoizedAddTo80(5)); // executes from cache
```

## 128. Memoization 2

We can utilize the closures to prevent usage of the global scopes to implement the memoization.

Is quite useful with implementation of dynamic programming.

example:

```jsx
// generic way to execute
function addTo80(n) {
	console.log("long time");
	return n + 80;
}

function memoizedAddTo80() {
	// using closures to create data for memoization cache .
	let cache = {};
	return function (n) {
		// if data is present in cache, then return it from cache
		if (n in cache) {
			console.log("getting from cache");
			return cache[n];
		} else {
			// if data no present in cache, then add result to cache and return it from cache
			console.log("taking longer route");
			cache[n] = n + 80;
			return cache[n];
		}
	};
}

console.log(memoizedAddTo80()(5)); // executes without cache
console.log(memoizedAddTo80()(5)); // executes from cache
```

## 129. Compose and Pipe

### Compose

Is system design principle which deals with relationship between components.

Conveys the principle that any sort of data transfer should be obvious.

Isn’t natively available to JavaScript but other libraries allows to use it.

example:

```jsx
// creating a composeer function
const compose = (f, g) => (data) => f(g(data));

// creating pure functions
const multiplyBy3 = (num) => num * 3;
const makePositive = (num) => Math.abs(num);

// implement composer functions with pure functions
const multiplyBy3AndAbsolute = compose(multiplyBy3, makePositive);

console.log(multiplyBy3AndAbsolute(-4)); // 12
```

### Pipe

Is fundamentally same as compose but the flow is opposite. In compose, the flow goes from left to right while in pipe, the flow goes from right to left.

It simply means the parameters which were passed first will be executed at last and vice versa.

example:

```jsx
// creating a pipe function
const pipe = (f, g) => (data) => g(f(data));

// creating pure functions
const multiplyBy3 = (num) => num * 3;
const makePositive = (num) => Math.abs(num);

// implement pipe functions with pure functions
const multiplyBy3AndAbsolute = pipe(multiplyBy3, makePositive);

console.log(multiplyBy3AndAbsolute(-4)); // 12
```

## 130. Arity

Is simply the number of arguments a function takes.

More parameter a function has, more complex it gets. Always prefer to get the parameter as low as possible.

## 131. The Answer to everything

The idea of functional programming is all about about separation of data and functions.

Effect and logic isn’t advised to perform at the same time. It may cause the hidden bugs.

keeping functions small, pure, and usable builds the complex implementation one by one.
