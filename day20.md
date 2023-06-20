**# Day 20**

- [Section 3: JavaScript Foundation II](#section-3-javascript-foundation-ii)
  - [47. this keyword](#47-this-keyword)
    - [Benefits of this keyword:](#benefits-of-this-keyword)
  - [48. Dynamic Scope vs Lexical Scope](#48-dynamic-scope-vs-lexical-scope)
    - [How to avoid dynamic scoping?](#how-to-avoid-dynamic-scoping)
  - [49. call(), apply(), bind()](#49-call-apply-bind)
    - [call()](#call)
    - [apply()](#apply)
    - [bind()](#bind)
    - [conclusion](#conclusion)
  - [51. bind() and currying](#51-bind-and-currying)
  - [54. Context vs Scope](#54-context-vs-scope)

# Section 3: JavaScript Foundation II

## 47. this keyword

`this` is the object that function is a property of

example:

`this` in web browser is window object.

`this` in NodeJS is global object.

A new instance of `this` is created for functions also when they are invoked.

example:

```jsx
const sampleObj = {
	name: "Pank",
	greet: function () {
		return "Hellooo " + this.name; // this refers to the sampleObj object
	},
};

console.log(sampleObj.greet()); // Hellooo Pank
```

### Benefits of this keyword:

1. Give methods access to their object.
2. Allows to execute the same code for multiple objects.

## 48. Dynamic Scope vs Lexical Scope

Everything in JavaScript is lexical scoped except for `this` keyword. It’s dynamically scoped.

For the Dynamic scope, it doesn’t matter where it’s written and how the function was called.

### How to avoid dynamic scoping?

Using arrow function which has lexical scope will solve the issue or bind the function with the this keyword.

Using arrow function is more common.

## 49. call(), apply(), bind()

### call()

Is used to invoke the function. It’s used all the time under the hood when a function is invoked.

example:

for a function `sayHello`, `sayHello.call()` is same as `sayHello()`

It also allows to extend the functionality of an object by borrowing methods and properties of other objects.

syntax: `methodToBorrowFrom.methodName.call(methodToBorrowInto, arguments)`

It accepts arguments separated by comma.

example:

```jsx
const wizard = {
	name: "Merlin",
	health: 50,
	heal(num1, num2) {
		return (this.health += num1 + num2);
	},
};

const archer = {
	name: "Robin hoood",
	health: 30,
};

console.log(archer); // { name: 'Robin hoood', health: 30 }

wizard.heal.call(archer, 30, 20); // extending the archer's functionality

console.log(archer); // { name: 'Robin hoood', health: 80 }
```

### apply()

Apply also does the same thing as `call()`

It accepts argument as an array unlike for `call()`, it would be simple comma separated.

example:

```jsx
const wizard = {
	name: "Merlin",
	health: 50,
	heal(num1, num2) {
		return (this.health += num1 + num2);
	},
};

const archer = {
	name: "Robin hoood",
	health: 30,
};

console.log(archer); // { name: 'Robin hoood', health: 30 }

wizard.heal.apply(archer, [30, 20]); // extending the archer's functionality

console.log(archer); // { name: 'Robin hoood', health: 80 }
```

### bind()

Unlike `call()` and `apply()` bind doesn’t run the function immediately but returns it. It allows us to store it and execute whenever it requires.

example:

```jsx
const wizard = {
	name: "Merlin",
	health: 50,
	heal(num1, num2) {
		return (this.health += num1 + num2);
	},
};

const archer = {
	name: "Robin hoood",
	health: 30,
};

console.log(archer); // { name: 'Robin hoood', health: 30 }

const healArcher = wizard.heal.bind(archer, 30, 20); // extending the archer's functionality
healArcher();

console.log(archer); // { name: 'Robin hoood', health: 100 }
```

### conclusion

`call()` and `apply()` are useful while borrowing methods from an objects while `bind()` is useful for us to call a function in future in certain context.

## 51. bind() and currying

Function currying is a technique where a function with multiple arguments is transformed into a sequence of functions, each taking a single argument. It allows you to create new functions by pre-filling some arguments of an existing function, resulting in a more specialized or partially applied function.

function currying allows to make the functions more specific and yet dynmamic.

example:

```jsx
// function currying
function multiply(a, b) {
	return a * b;
}

let multiplyByTwo = multiply.bind(this, 2);

console.log(multiplyByTwo(9));
```

## 54. Context vs Scope

scope is function based and says what is in the variable environment while context is more about object based and what is the value of `this` keyword which is reference to the object that owns that current executing code.

Context is defined by how a function is invoked with the value of `this` keyword and scope refers to the visibility of the variables.
