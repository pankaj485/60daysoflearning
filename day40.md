**# Day 40**

- [Section 15: Appendix II: Intermediate JavaScript](#section-15-appendix-ii-intermediate-javascript)
  - [213. ES6 and ES5](#213-es6-and-es5)
  - [214. Advanced functions](#214-advanced-functions)
  - [215. Advanced Arrays](#215-advanced-arrays)
    - [Map](#map)
    - [Filter](#filter)
    - [Reduce](#reduce)

# Section 15: Appendix II: Intermediate JavaScript

## 213. ES6 and ES5

ES stands for ecmascript which is a standard of JavaScript.

ES6 is a version of standard of JavaScript.

Babel allows to compiles a version of JavaScript into another.

Features introduced with the ES6:

1. `let` and `const` to declare variables and constants. It allows block level scopes.
2. object destructuring

   example:

   ```jsx
   // declaring object "obj"
   const obj = {
   	name: "mark",
   	role: "admin",
   	devie: "linux",
   };

   // destructring, assigning to different keyword of "obj"
   const { devie, name: uname, role } = obj;

   // printing directly from destructured value
   console.log(devie);
   console.log(uname);
   console.log(role);
   ```

3. Allows to use a single value when key and value is expected to be same for the object items.

   example:

   ```jsx
   const username = "mark";
   const role = "admin";
   const devie = "linux";

   // assigning values with single keyword to objects
   const obj = {
   	username,
   	role,
   	devie,
   };

   console.log(obj);
   // output: { username: 'mark', role: 'admin', devie: 'linux' }
   ```

4. Template string

   Allows to perform concatenation of strings and expression in much more cleaner way.

   example:

   ```jsx
   const username = "mark";
   const role = "admin";
   const device = "linux";

   // normal concatenation vs using string literal
   const normalConcat = "username: " + username + "role: " + role + "device: " + device;
   const stringLiteral = `username: ${username} role: ${role} device: ${device}`;
   ```

5. Default arguments

   Allows to have default arguments on the functions which will be used if no arguments are passed while invoking the function.

   example:

   ```jsx
   // using default arguments with function
   function printInfo(name = "mark", age = "20", role = "admin") {
   	console.log(`Hi ${name}, you are ${age} years old and your role is ${role}`);
   }

   // calling function without arguments
   printInfo(); // output: Hi mark, you are 20 years old and your role is admin
   ```

6. Arrow functions

   Allows to write functions in much more easier way. can be really useful while writing callback functions.

   example:

   ```jsx
   // usual function declaration
   const normalHello = function (name) {
   	console.log(`"hello" ${name}, nice to meet you!`);
   };

   // arrow function declaration
   const arrowHello = (name) => {
   	console.log(`"hello" ${name}, nice to meet you!`);
   };
   ```

## 214. Advanced functions

Usual functions can be easily replaced with the arrow functions.

Closures are superpower of the functions. It allows to access the parent scope from child function scopes.

Function currying allows to use the parameters of the function one at a time. Each execution returns a function which takes upcoming parameter

example:

```jsx
// currying function
const curriedMultiply = (a) => (b) => a * b;

console.log(curriedMultiply(6)(3)); // output: 18
```

Function compose allows to use the functions one by one

example:

```jsx
// compose function
const composedIncrement = (a, b) => (c) => a(b(c));
const increment = (num) => num + 1;

console.log(composedIncrement(increment, increment)(3)); // output: 5
```

It’s always a good practice to use function in such a way that it doesn’t affect the outside scope scope of the function.

## 215. Advanced Arrays

### Map

Allows to iterate each element of an array and returns a new array. It doesn’t change the original array item.

example:

```jsx
const numbers = [1, 2, 4, 5, 7, 6];

// map
const double = numbers.map((number) => {
	return number * 2;
});

console.log(double); // outuput: [ 2, 4, 8, 10, 14, 12 ]
```

### Filter

Allows to filter the array item by iterating through the array and return value based on condition.

example:

```jsx
const numbers = [1, 2, 4, 5, 7, 6];

// filter
const evenNumbers = numbers.filter((number) => {
	// if the current number matches the condition then return it else don't
	return number % 2 === 0;
});

console.log(evenNumbers); // outuput: [ 2, 4, 6 ]
```

### Reduce

Is advanced iteration way which allows to use map and reduce both. It returns a single value.

The reducer walks through the array element-by-element, at each step adding the current array value to the result from the previous step (this result is the running sum of all the previous steps) — until there are no more elements to add.

Includes `accumulator` and `number` Number is the currently iterated number. Accumulator is the storage of the information that happens inside of the body of the function. The value of the accumulator is persisted throughout the iteration. The accumulator is used for the first iteration.

The default value of accumulator can be defined after the function.

example:

```jsx
const numbers = [1, 2, 4, 5, 7, 6];

// add
const add5 = numbers.reduce((acc, num) => {
	return acc + num;
}, 5);

console.log(add5);
```

mdn reference: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/reduce
