**# Day 9**

- [Section 6: Building Objects](#section-6-building-objects)
  - [58. Function Constructors, new, and the history of JavaScript](#58-function-constructors-new-and-the-history-of-javascript)
    - [history of Js](#history-of-js)
    - [function constructor](#function-constructor)

## 56. Everything is an Object (or a primitive)

Execept of the base object, evertything has prototypes.

The base object is the most bottom part of the prototype chain.

All objects, functions, arrays will have prototype property set built in. which can be accessed with `functionName.__proto__`

Based on the data types, the prototype can have different property which can be used with all of it’s type.

The pototype of prototype is object.

The prototype of object is also object.

It all boils down to object in the end.

## 57. Reflection and Extend

### Reflection

An object can look at itself, listing and changing it’s properties and methods. The ability is called reflection.

A common use case of it is iterating throgh the items of an array or an objcet.

example:

```jsx
let person = {
	firstName: "default",
	lastName: "default",
	getFullName: function () {
		return this.firstName + " " + this.lastName;
	},
};

// iterating and still checking for the existance of the item
for (var prop in person) {
	if (person[prop]) {
		console.log(prop);
	}
}
```

### extend

allows to add methods and properties to an object from other objects.

`extend` is usually a high level function that copies the prototype of a new subclass that you want to extend from the base class.

So you can do something like:

```jsx
extend(Fighter, Human);
```

And the `Fighter` constructor/object will inherit the prototype of `Human`, so if you define methods such as `live` and `die` on `Human` then `Fighter` will also inherit those.

`.extend` isn't built-in but often provided by a library such as jQuery or Prototype.

It’s differnet from `extends` .

blog on extends: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Classes/extends

# Section 6: Building Objects

## 58. Function Constructors, new, and the history of JavaScript

### history of Js

JavaScript named so to attract the Java Devs.

The `new` keyword was used to create object from class in Java which is then implemented to JavaScript also.

`new` is an operator which creates an empty object and invokes the function, creates the execution context, and invokes the function. Basically it allows to create an object using function.

### function constructor

Function constructor is a normal function that is used to construct objects. The `this` variable points a new empty object, and that obejct is returend from the function automatically.

example:

```jsx
class Person {
	constructor(firstName, lastName) {
		this.firstName = firstName;
		this.lastName = lastName;
	}
}

// creating new object
let person1 = new Person("Mark", "manson");
console.log(person1);
// output: Person { firstName: 'John', lastName: 'Doe' }
```
