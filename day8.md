**# Day 8**

- [Section-3 Object Oriented JavaScript and Prototypal Inheritance.](#section-3-object-oriented-javascript-and-prototypal-inheritance)
  - [54. Conceptual Aside: Classical vs Prototypal inheritance](#54-conceptual-aside-classical-vs-prototypal-inheritance)
    - [Inheritance](#inheritance)
    - [Prototypal inheritance](#prototypal-inheritance)
  - [55. Understanding the Prototypes](#55-understanding-the-prototypes)

## 52. Functional Programming

JavaScript allows to have first class functions which allows it to utilize functional programming.

Allows functions to use function as a parameter, pass one function to another, return function.

Can simplify and makes the code more finer and more reusable. Is very much applicable with mathematical functions and filtration kind of usage.

As a downside, functional programming requires a large memory space. As it does not have state, you need to create new objects every time to perform actions.

detailed blog on functional programing: https://www.tutorialspoint.com/functional_programming/functional_programming_introduction.htm

## 53. Functional Programming - Part 2

Functional programming is used quite alot in libraries. example: loadash, underscore.js. It includes methods like `map()` and `filter()`

Is quite used in open source proejcts also.

# Section-3 Object Oriented JavaScript and Prototypal Inheritance.

## 54. Conceptual Aside: Classical vs Prototypal inheritance

### Inheritance

Is when one object can get access of properties and methods of another object.

Is a way to share methods and properties of object.

Classical Inheritance has many concepts which deals with inheritance like friend, protected, private, interface which can make it confusing.

### Prototypal inheritance

Is more simpler than classic Inheritance.

Is more extensible and easy to understand.

Implementation can be different from other programming languages.

## 55. Understanding the Prototypes

Is a JavaScript language specific feature.

All objects including functions in JavaScript have a object prototype property called `proto`.

Is an object that stands by own and objects gets their properties from it and can access them.

The prototype can also have link to the other prototype object.

prototype chain in JavaScript

When object method or property is called then the JavaScript engine will look into it’s own sope at first. If it’s not there then it will look into the prototype later on.

Directly using the prototypes isn’t advised at it can slow down the program.

To access the prototype directly, use `object.__person__ = other_object`

example:

```jsx
let person = {
	firstName: "default",
	lastName: "default",
	getFullName: function () {
		return this.firstName + " " + this.lastName;
	},
};

let john = {
	firstName: "John",
};

/* NOTE: not at all advised to use */
// one obejct using method of other object by directly accesing prototype object
john.__proto__ = person;

console.log(john.getFullName()); // output: John default
```
