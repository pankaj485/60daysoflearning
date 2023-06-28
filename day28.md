**# Day 28**

- [Section 6: Object Oriented Programming](#section-6-object-oriented-programming)
  - [111. 4 Pillars of OOP](#111-4-pillars-of-oop)
    - [Encapsulation](#encapsulation)
    - [Abstraction](#abstraction)
    - [Inheritance](#inheritance)
    - [Polymorphism](#polymorphism)
    - [Advantages of OOP](#advantages-of-oop)
  - [112. Exercise: OOP and Polymorphism](#112-exercise-oop-and-polymorphism)

# Section 6: Object Oriented Programming

## 111. 4 Pillars of OOP

4 pillars of OOP are:

### Encapsulation

Wrap code into blocks which are related to each other using the properties and methods we make available.

It makes easier to read and maintain.

### Abstraction

Is way of hiding the complexity from the user and only expose the necessary parts of it.

It reduces the complexity and allows to use public and private inheritances.

### Inheritance

Allows to save memory by saving memory space, reduces the complexity and duplication

Allows one class to access properties and methods defined in the other class.

### Polymorphism

Allows to make the methods dynamic and act differently based on the data fed into it.

It simply means to appear in many forms usually with method overriding where same method acts differently or method overloading which adds extra fields or parameters to the method to add onto what that method can do.

It has ability to process data differently based on data type and class.

Is useful since it doesn’t require to write it from scratch but can easily extend the existing idea.

### Advantages of OOP

1. Clear and understandable
2. Easy to extend
3. Easy to maintain
4. Memory efficient
5. Allows to follow DRY principles

## 112. Exercise: OOP and Polymorphism

exersise repel: https://replit.com/@aneagoie/OOP-exercise#index.js

my solution:

```jsx
class Character {
	constructor(name, weapon) {
		this.name = name;
		this.weapon = weapon;
	}
	attack() {
		return "atack with " + this.weapon;
	}
}

// extending the "Character" class by inheriting it with "Queen" class
class Queen extends Character {
	constructor(name, weapon, type) {
		super(name, weapon);
		this.type = type;
	}

	// overriding the super class "attack" method
	attack() {
		return `I am the ${this.name} of ${this.weapon}, now bow down to me!`;
	}
}

//Polymorphism--
// Extend the Character class to have a Queen class. The output of the below code should be:
const victoria = new Queen("Victoria", "army", "hearts"); // create a new instace with the queen having (name, weapon, type). Type inlcudes: 'hearts', 'clubs', 'spades', 'diamonds'

console.log(victoria.attack()); // will console.log the attack() method in Character class AND will return another string: 'I am the Victoria of hearts, now bow down to me! '
```
