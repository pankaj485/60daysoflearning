**# Day 26**

- [Section 6: Object Oriented Programming](#section-6-object-oriented-programming)
  - [104. Object.create() vs Class](#104-objectcreate-vs-class)
  - [105. this - 4 ways](#105-this---4-ways)
    - [new binding this](#new-binding-this)
    - [implicit binding](#implicit-binding)
    - [explicit binding](#explicit-binding)
    - [arrow function](#arrow-function)
  - [106. Inheritance](#106-inheritance)
  - [107. Inheritance 2](#107-inheritance-2)

# Section 6: Object Oriented Programming

## 104. Object.create() vs Class

There is no right or wrong with any of those.

Object.create() will utilize the pure prototypal inheritance right while writing the class while a class will do it under the hood.

## 105. this - 4 ways

### new binding this

example:

```jsx
// new binding this
function Person(name, age) {
	this.name = name;
	this.age = age;
}
```

### implicit binding

example:

```jsx
// implicit binding
const person = {
	name: "Karen",
	age: 40,
	hi() {
		console.log("hi, " + this.name);
	},
};
```

### explicit binding

example:

```jsx
// explicit binding
const person3 = {
	name: "Karen",
	age: 40,
	// explicitely using bind to bind the global object
	hi: function () {
		console.log("hi: ", this.setTimeout);
	}.bind(globalThis),
};
```

### arrow function

example:

```jsx
// arrow function
const person4 = {
	name: "Karen",
	age: 40,
	hi: function () {
		var inner = () => {
			console.log("Hi " + this.name);
		};
		return inner;
	},
};
```

## 106. Inheritance

Allows classes to access properties and method of other class

The class from where the properties and methods are accessed are called as super classes

example:

```jsx
// super class
class Character {
	constructor(name, weapon) {
		this.name = name;
		this.weapon = weapon;
	}
	attack() {
		return "attack with " + this.weapon;
	}
}

// children class "Elf" inheriting super class "Character"
class Elf extends Character {
	constructor(name, weapon, type) {
		// initializing the super class constructor on the inherited class
		super(name, weapon);
		this.type = type;
	}
}

const dolny = new Elf("Dolby", "cloth", "house");
console.log(dolny); // Elf { name: 'Dolby', weapon: 'cloth', type: 'house' }
```

## 107. Inheritance 2

Under the hood, the execution of inheritance is based on the prototypal inheritance and the prototype chains.

Inherit will not copy the properties and methods to the class but it will link them up to prototype chain with the properties and methods. It will link to the same memory space.
