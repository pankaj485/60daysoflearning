**# Day 41**

- [Section 15: Appendix II: Intermediate JavaScript](#section-15-appendix-ii-intermediate-javascript)
  - [216. Advanced Objects](#216-advanced-objects)
    - [reference type](#reference-type)
    - [context](#context)
    - [instantiation](#instantiation)
  - [217. ES7](#217-es7)
    - [includes](#includes)
    - [exponential function](#exponential-function)
  - [218. ES8](#218-es8)
    - [string padding](#string-padding)
    - [trailing comma and functions parameter list in calls](#trailing-comma-and-functions-parameter-list-in-calls)
    - [Object.values](#objectvalues)
    - [Object.entries](#objectentries)
  - [220. ES10](#220-es10)
    - [Array.flat()](#arrayflat)
    - [Array.flatmap()](#arrayflatmap)
    - [trimStart and trimEnd](#trimstart-and-trimend)
    - [formEntries](#formentries)
    - [try catch block](#try-catch-block)

# Section 15: Appendix II: Intermediate JavaScript

## 216. Advanced Objects

### reference type

Objects are reference types in JavaScript.

Objects are non-primitive data types.

Arrays are special objects. The same applies to it as objects too.

example:

```jsx
let object1 = { value: 10 };
let object2 = object1;
let object3 = { value: 10 };

console.log(object1 === object2); // true (both are referencing to same memory location)
console.log(object1 === object3); // false (both are not referencing to same memory location)
```

### context

context is the object environment we are inside of.

for example, in the global environment, it’s window but for inside of an object, it will the object’s scope.

### instantiation

Is just how we use inheritance with extend keyword, constructor function and super keyword.

example:

```jsx
// parent class
class Player {
	constructor(name, type) {
		(this.name = name), (this.type = type);
	}
	introduce() {
		return `Hi I'm ${this.name}, I'm a ${this.type}`;
	}
}

// children class inheriting from parent class
class Wizard extends Player {
	constructor(name, type) {
		// extending the properties from parent class
		super(name, type);
	}
	printType() {
		return `My agent type is ${this.type}`;
	}
}

// instantiating a new object from a class
const wizard1 = new Wizard("Shelly", "Healer");

// utitlizng the instiantiated object
console.log(wizard1);
console.log(wizard1.introduce());
console.log(wizard1.printType());

// output
// Wizard { name: 'Shelly', type: 'Healer' }
// Hi I'm Shelly, I'm a Healer
// My agent type is Healer
```

## 217. ES7

Released in 2017

Features included on ES7 are:

### includes

Is a string and array method which allows to check if a particular set of character or item is present on string or an array.

Gives boolean output value.

example:

```jsx
const items = ["data", "variable", "paramter", "context", "scope"];
const item = "database cluster";

// includes with array
console.log(items.includes("data"));

// includes with item
console.log(item.includes("data"));

// output
// true
// false
```

### exponential function

allows to easily perform exponential operation of numbers.

example:

```jsx
// calculating squrae exponential of 5 using exponential operator
console.log(5 ** 2);

// output: 25
```

## 218. ES8

Features introduced with ES8:

### string padding

Allows to add padding of spaces around the string.

uses methods `.padStart` and `.padEnd`

example:

```jsx
let greeting = "hello";

greeting.padStart(5);
greeting.padEnd(5);

console.log(greeting);

// output
// "     hello     "
```

### trailing comma and functions parameter list in calls

Allows to add comma at the end of the function parameter call and will still be a valid syntax which allows to reduce the error and is easier to add a new parameter.

example:

```jsx
// using trailing comma in function parameter list
const function = (a, b, c, d,) => {
	console.log("nice")
}
```

### Object.values

Allows to iterate through the values only of the objects.

example:

```jsx
let obj = {
	username: "hello",
	key: "val",
	item: "yes",
};

Object.keys(obj).forEach((key, index) => {
	console.log(`key: "${key}"`);
});

// output
// key: "username"
// key: "key"
// key: "item"
```

### Object.entries

Allows to iterate through the object just like an array.

example:

```jsx
let obj = {
	username: "hello",
	key: "val",
	item: "yes",
};

Object.entries(obj).forEach((value, item) => {
	console.log(`key: "${value[0]}", value: "${value[1]}"`);
});

// output
// key: "username", value: "hello"
// key: "key", value: "val"
// key: "item", value: "yes"
```

## 220. ES10

Is 2019 version of JavaScript

Features introduced with ES10:

### Array.flat()

Allows to convert a nested array into a single array.

By default, it flattens 1 level of nesting but a particular nesting value can be used.

It also cleans up the array by removing the empty entry.

example:

```jsx
const nestedArray = [3, 4, , , , , [4, , , 6, [8, 6]]];

console.log(nestedArray);
console.log(nestedArray.flat(5));

// output:
// [ 3, 4, <4 empty items>, [ 4, <2 empty items>, 6, [ 8, 6 ] ] ]
// [ 3, 4, 4, 6, 8, 6 ]
```

### Array.flatmap()

Allows to use the conventional `.map` array function with the nested array of one level and allows to do operation.

example:

```jsx
const numbers = [1, 2, [3, 5, [6, 7]], 4];

console.log(numbers.flatMap((item) => item + "hello"));

// output:
// [ '1hello', '2hello', '3,5,6,7hello', '4hello' ]
```

### trimStart and trimEnd

Allows to remove the blank spaces around the string

example:

```jsx
const randomString = "  hello      ";

console.log(randomString.trimStart());
console.log(randomString.trimEnd());

// output:
// 'hello      '
// '  hello'
```

### formEntries

Allows to transform a list of key value pair into an object.

example:

```jsx
// defining normal key value pair
const keyValues = [
	["username", "pank"],
	["age", 24],
	["role", "admin"],
];

// pass an array and transform it to an object
const transformedObject = Object.fromEntries(keyValues);

console.log(transformedObject);

// output
// { username: 'pank', age: 24, role: 'admin' }
```

### try catch block

Is already covered previously.

Is useful to handle the error prone conditions.

But with ES10, error parameter is not necessary to use with the try catch block and is an optional usage.

example:

```jsx
// conventional try catch
try {
	console.log("conventional try");
} catch (error) {
	console.log("conventional catch");
}

// ES10 try catch (without error)
try {
	console.log("ES10 try");
} catch {
	console.log("ES10 catch");
}
```
