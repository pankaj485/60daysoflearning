**# Day 42**

- [Section 15: Appendix II: Intermediate JavaScript](#section-15-appendix-ii-intermediate-javascript)
  - [221. Advanced Loops](#221-advanced-loops)
    - [for of](#for-of)
    - [for in](#for-in)
  - [222. ES2020 Part 1](#222-es2020-part-1)
    - [BigInt](#bigint)
  - [223. ES2020 Part 2](#223-es2020-part-2)
    - [Optional chaining Operator (?.)](#optional-chaining-operator-)
  - [224. ES2020 Part 3](#224-es2020-part-3)
    - [Nullish coalescing Operator (??)](#nullish-coalescing-operator-)
  - [225: ES2020: globalThis](#225-es2020-globalthis)
    - [globalThis](#globalthis)
  - [226: ES2021](#226-es2021)
    - [replaceAll](#replaceall)
  - [227: Debugging](#227-debugging)
  - [228: Modules](#228-modules)

# Section 15: Appendix II: Intermediate JavaScript

## 221. Advanced Loops

### for of

Works with iterables (array and string).

Allows to iterate instance of the iterable.

example:

```jsx
const sampleArrayData = ["one", "two", "three", "four", "five"];
const sampleStringData = "hello";

// for of with a string
for (let currentChar of sampleStringData) {
	console.log(currentChar);
}

// for of with an array
for (let currentData of sampleArrayData) {
	console.log(currentData);
}

// output
// h
// e
// l
// l
// o
// one
// two
// three
// four
// five
```

### for in

Works with objects.

Allows to enumerate (loop over) an object and get the properties.

example:

```jsx
const sampleObject = {
	name: "charile",
	role: "shooter",
	health: 100,
	age: 12,
};

for (let currentItem in sampleObject) {
	console.log(currentItem);
}

// output
// name
// role
// health
// age
```

Enumerable and iterable are for objects and arrays respectively.

[The Difference Between Iterable And Enumerable In JavaScript](https://dilshankelsen.com/difference-between-iterable-enumarable-in-javascript/)

## 222. ES2020 Part 1

### BigInt

Is a new type in JavaScript.

JavaScript has MAX_SAFE_INTEGER. Calculation starts to break down beyond the value. It doesn’t perform the calculation as expected.

bigint allows to perform calculations between larger numbers.

To use bigint, simply use letter `n` after the number.

mdn reference: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/BigInt

example:

```jsx
console.log(1n + 2n);
```

## 223. ES2020 Part 2

### Optional chaining Operator (?.)

Allows to do value check on the object properties.

example:

```jsx
const sampleObject = {
	userData: {
		name: "mark",
		address: "mars",
		distance: "far",
		age: 66,
	},
};

// normal value check with if
if (sampleObject.userData && sampleObject.userData.name) {
	console.log(sampleObject.userData.name);
}

// value check with Optional chaining Operator
console.log(sampleObject?.userData?.name);
```

## 224. ES2020 Part 3

### Nullish coalescing Operator (??)

Is alternative to the OR operator.

Unlike in OR operator, It allows to filter if the value is nullish or undefined instead of truthy and falsy values.

example:

```jsx
const sampleObject = {
	userData: {
		name: "mark",
		address: "mars",
		distance: "far",
		age: 66,
		power: 0,
	},
};

// value checking with conventional OR (truthy and falsy check)
let powerWithOr = sampleObject?.userData?.power || "no power";

// value checking with Nullish coalescing (undefined and null check)
let powerWithCoalescing = sampleObject?.userData?.power ?? "no power";

console.log(powerWithOr);
console.log(powerWithCoalescing);

// output
// no power
// 0
```

## 225: ES2020: globalThis

### globalThis

works outside of the browser like in NodeJS unlike of window.

It contains the data same as global but it exists on both NodeJS and browser which unifies the code base.

Node `>V14` is required to use it.

## 226: ES2021

### replaceAll

Allows to replace all the instances of the particular set of characters inside of a string to the new value.

Unlike in `replace`, it allows to replace all the instances of the characters instead of the first only.

example:

```jsx
const newData = "hi hello hi this is hi okay hi yes";

console.log(newData.replaceAll("hi", "sup"));
// output
// sup hello sup tsups is sup okay sup yes
```

## 227: Debugging

Useful strategy to work with debugging:

1. print the values, check if the expected values are received.
2. use meaningful variable naming.
3. use meaningful comments.
4. attach debugger by using `debugger;` which allows to stop the current process and stops at the middle of the execution where it started.
   It allows to observe the flow of the program step by step.

## 228: Modules

Is already covered in the previous lectures.

Is basically is a way to manage the files and modules and resolve the dependency resolution and by not polluting the global namespace.

ES6 and commonJS are the 2 major way to do it. commonJS is the older way.
