**# Day 10**

- [59. Function Constructors and ‘.prototype’](#59-function-constructors-and-prototype)
  - [How to set the prototype?](#how-to-set-the-prototype)
- [60. Dangerous Aside: ‘new’ and functions](#60-dangerous-aside-new-and-functions)
- [61. Conceptual Aside: Built-in Function Constructors](#61-conceptual-aside-built-in-function-constructors)
- [62. Dangerous Aside: Built-In Function Constructors](#62-dangerous-aside-built-in-function-constructors)
- [63. Dangerous Aside: Arrays and for..in](#63-dangerous-aside-arrays-and-forin)

## 59. Function Constructors and ‘.prototype’

### How to set the prototype?

when function constructor is used, it already sets the prototype.

All functions has prototype property which starts as empty object. It’s used by new operator only. It’s not the prototype of the function but the prototype of the object. New methods and properties can be added to it.

If the method is added to the prototype then it will be chained to the memory space only when it’s called but if it’s added in the function body then it will create the method for all the new objects created from it.

example: creating objects and setting prototypes

```jsx
class Person {
	constructor(firstName, lastName) {
		this.firstName = firstName;
		this.lastName = lastName;
	}
}

// setting prototype method
Person.prototype.getFullName = function () {
	return this.firstName + " " + this.lastName;
};

// creating new object
let person1 = new Person("John", "Doe");

// accessing prototype method
console.log(person1.getFullName());

// output: John Doe
```

## 60. Dangerous Aside: ‘new’ and functions

The `new` keyword is kind of silly if the convection is not well followed.

It may lead to unintentional errors if not used well.

While dealing with function constructors, always use the capital letter of the first letter of the keyword.

In present there are better ways to create them.

## 61. Conceptual Aside: Built-in Function Constructors

There are already existing some of the function constructors.

Based on that, various methods can be accessed outside of box.

They creates objects which has primitive values like string, number, boolean.

example:

```jsx
let a = new String("hello");
// String() is a function constructor
// It will have primitive value of "hello"
// it also has built in methods like .length, .includes, .slice and so on...
```

The built in function constructors methods can also be extended. But can’t override the existing properties and methods.

In general it’s not advised to use this way as the type of primitive can be the problem.

example:

```jsx
// addging new method which verifies if string length is greater than the limit
String.prototype.hassLegthGreaterThan = function (limit) {
	return this.length > limit;
};

let a = new String("hello");

console.log(a.hassLegthGreaterThan(3)); // true
```

## 62. Dangerous Aside: Built-In Function Constructors

It can be dangerous as it is directly dealing with the primitive types and may cause confusion and may create bugs on the way.

The constructors doesn’t really create primitive types. Can be used used in some times but often times creates more confusion.

example:

```jsx
var a = 3; // Number type primitive
var b = new Number(3); // creates object but has Number primitive

console.log(a == b); // true (only values are checked)
console.log(a === b); // false (type is checked along with value)

console.log(typeof a); // number
console.log(typeof b); // object
```

## 63. Dangerous Aside: Arrays and for..in

An array is also an object. It is different than in other programming languages. Each item is key value pair.

Use standard iterators like for loops instead of for..in in case of array.
