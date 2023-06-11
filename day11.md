**# Day 11**

- [64. Object.create and Pure Prototypal Inheritance](#64-objectcreate-and-pure-prototypal-inheritance)
  - [Pure prototypal inheritance](#pure-prototypal-inheritance)
  - [ployfill](#ployfill)
- [64. ES6 and Classes](#64-es6-and-classes)
- [66. Initialization](#66-initialization)
- [67. typeof, instanceof, and figuring out what something is](#67-typeof-instanceof-and-figuring-out-what-something-is)
  - [typeof](#typeof)
  - [instance of](#instance-of)
- [68. Strict mode](#68-strict-mode)

## 64. Object.create and Pure Prototypal Inheritance

Function constructor was designed to mimic the Java and it utilizes the Prototypal inheritance instead of classical inheritance.

### Pure prototypal inheritance

Is based on prototype concept and prototype chain.

How it works: initially an object is created and based on that object, a new object is created and override the existing properties from the base object.

example:

```jsx
var person = {
	firstName: "Defualt",
	lastName: "Default",
	greet: function () {
		return "Hello " + this.firstName + " " + this.lastName;
	},
};

// using prototype to create a new object
let john = Object.create(person);

// overriding the existing property
john.firstName = "John";

// calling the methods
console.log(john.greet());

// outupt: Hello John Default
```

### ployfill

Is the part of the code which adds the feature which the engine may not have out of the box.

use case: working with old code to support the new feature.

Allows to create the extend object properties freely without relying on complex structures.

example:

If `Object.create` method is not available then create it and mount it to global so that it can be used.

```jsx
if (!Object.create) {
	Object.create = function (o) {
		if (arguments.length > 1) {
			throw new Error("Object.create implementation" + "only accepts the first parameter");
		}
		function F() {
			// creating prototype of the existing object
			F.prototype = o;
			return new F();
		}
	};
}
```

## 64. ES6 and Classes

Is 2015 version of JavaScript which allows to create objects from classes in different way than other programing language.

In JavaScript, classes are also objects unlike other programing languages. From that object new objects are created.

Has become and standard and is more widely used.

In ES6, `extends` keyword is used to along with constructor function with `super` keyword to set the prototypes. Under the hood is same implementation but ES6 allows these to be used as syntactic sugar.

example:

```jsx
// setting prototype with 'extends' keyword
class InformalPerson extends Person {
	constructor(firstName, lastName) {
		super(firstName, lastName);
	}

	gret() {
		return "hello" + this.firstName;
	}
}
```

## 66. Initialization

Is when values are provided to the variables at the time of declaration

While using large initialization, often times comma or brackets are not used or misused, using equal instead of colons which will cause error message like `unexpected tokens` in general way.

## 67. typeof, instanceof, and figuring out what something is

### typeof

allows to access what data type the provided item is

typeof undefined is undefined

typeof null is object which is known bug ever since

example:

```jsx
var a = 3;
var b = "hello";
var c = {};
var d = [];

console.log(typeof a); // number
console.log(typeof b); // string
console.log(typeof c); // object
console.log(typeof d); // object (arrays are obejcts in js)
console.log(Object.prototype.toString.call(d)); // [object Array]
```

### instance of

The **`instanceof`** operator tests to see if the `prototype` property of a constructor appears anywhere in the prototype chain of an object. The return value is a boolean value.

example:

```
function Car(make, model, year) {
  this.make = make;
  this.model = model;
  this.year = year;
}
const auto = new Car('Honda', 'Accord', 1998);

console.log(auto instanceof Car);
// Expected output: true

console.log(auto instanceof Object);
// Expected output: true

```

## 68. Strict mode

Process the code in more strict manner.

Allows to be strict by only allowing to use the variables

to use strict mode use `"use strict"` on top of the file or function.

Strict mode makes several changes to normal JavaScript semantics:

1. Eliminates some JavaScript silent errors by changing them to throw errors.
2. Fixes mistakes that make it difficult for JavaScript engines to
   perform optimizations: strict mode code can sometimes be made to run
   faster than identical code that's not strict mode.
3. Prohibits some syntax likely to be defined in future versions of ECMAScript.

example:

```jsx
function sayHello() {
	"use strict";
	var message = "helloooo";
	console.log(message);
}

sayHello();
// output: messagew is not defined (isn't declared but used )
```

MDN reference: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Strict_mode
