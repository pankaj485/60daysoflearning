**# Day 25**

- [Section 6: Object Oriented Programming](#section-6-object-oriented-programming)
  - [98. OOP1: Factory Functions](#98-oop1-factory-functions)
    - [Factory Functions](#factory-functions)
  - [99. OOP2: Object.create()](#99-oop2-objectcreate)
  - [100. OOP3: Constructor Functions](#100-oop3-constructor-functions)
  - [102. Funny thing about JavaScript](#102-funny-thing-about-javascript)
  - [103. OOP4: ES6 Classes](#103-oop4-es6-classes)
    - [Instance](#instance)

# Section 6: Object Oriented Programming

## 98. OOP1: Factory Functions

### Factory Functions

Functions which allows to create objects.

example:

```jsx
function createElf(name, weapon) {
	return {
		name,
		weapon,
		attack() {
			return "attack with " + weapon;
		},
	};
}

const peter = createElf("Peter", "stones");
console.log(peter.attack());
```

## 99. OOP2: Object.create()

It allows to create link between two functions by using prototypal inheritance.

example:

```jsx
const elfFunctions = {
	attack() {
		return "attack with " + this.weapon;
	},
};

function createElf(name, weapon) {
	// creating a new object which has prototype chain which includes the "elfFunctions" object
	let newElf = Object.create(elfFunctions);
	newElf.name = name;
	newElf.weapon = weapon;

	return newElf;
}

const peter = createElf("Peter", "stones");
console.log(peter.attack());
```

## 100. OOP3: Constructor Functions

Allows to create objects from a blueprint function. It usually starts with capital letter.

While creating an object from constructor function, `new` keyword has to be used.

Any functions invoked with `new` keyword is constructor function.

example:

```jsx
// constructor function
function Elf(name, weapon) {
	this.name = name;
	this.weapon = weapon;
}

// adding function to the constructor function with prototype chain
Elf.prototype.attack = function () {
	return "attack with " + this.weapon;
};

// usinig constructor function to create new object
const peter = new Elf("peter", "stones");
```

## 102. Funny thing about JavaScript

with the exception of `null` and `undefined`, everything has constructor functions.

## 103. OOP4: ES6 Classes

With ES6 classes, it allows to replace the constructor functions with `Class`

The implementation under the hood actually is constructor function but using class, it provides the syntactic sugar.

example:

```jsx
class Elf {
	constructor(name, weapon) {
		this.name = name;
		this.weapon = weapon;
	}
	attack = function () {
		return "attack with " + this.weapon;
	};
}

const peter = new Elf("peter", "stones");
```

### Instance

Instance is when an object is create from a class.

Object is an instance of a class

In above example, `peter` is an instance of `Elf`

Everything is still object in JavaScript including the classes.

To implement the classes, it still uses the constructor function to implement it under the hood. It’s still prototypal inheritance.
