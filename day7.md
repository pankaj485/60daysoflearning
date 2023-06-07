**# Day 7**

- [49. Framework Aside: Function Factories](#49-framework-aside-function-factories)
- [50. Closures and Callbacks](#50-closures-and-callbacks)
  - [callback functions](#callback-functions)
- [51. call(), apply(), and bind()](#51-call-apply-and-bind)
  - [bind()](#bind)
  - [call()](#call)
  - [apply()](#apply)
  - [Function borrowing with apply](#function-borrowing-with-apply)
  - [function currying with bind.](#function-currying-with-bind)

## 49. Framework Aside: Function Factories

With closures functions can be invoked more flexibly by relying on the execution context and memory space of the functions above one functions execution context.

The implementation is all about the language feature.

example:

```jsx
function makeGreeting(language) {
	// the returned function will still have access to the language parameter due to closure
	return function (firstName, lastName) {
		if (language == "en") {
			console.log("hello " + firstName + " " + lastName);
		}
		if (language == "es") {
			console.log("hola " + firstName + " " + lastName);
		}
	};
}

var greetEnglish = makeGreeting("en");
var greetSpanish = makeGreeting("es");

// each function call have own closure which means each fucntions will have own outer reference memory space
greetEnglish("John", "Doe"); // hello John Doe
greetEnglish("John", "Doe"); // hola John Doe
```

## 50. Closures and Callbacks

`setTimeOut` like functions always uses closures and callbacks together.

example:

```jsx
function sayHiLater() {
	var greeting = "Hi";

	setTimeout(() => {
		// execution context of setTimeout doesn't has direct access to "greeting" variable but is accessing it with closure
		console.log(greeting);
	}, 3000);
}

sayHiLater();
```

### callback functions

A callback is a function passed as an argument to another function. This technique allows a function to call another function.

A callback function can run after another function has finished

example:

```jsx
function greeting(name) {
	alert(`Hello, ${name}`);
}

function processUserInput(callback) {
	const name = prompt("Please enter your name.");
	callback(name);
}

processUserInput(greeting);
```

more on callback functions: https://developer.mozilla.org/en-US/docs/Glossary/Callback_function

## 51. call(), apply(), and bind()

functions are special objects which is has methods and is invoke able .

All functions has access to `call` , `apply`, and `bind` methods. All of which have to do with `this` variable and the arguments passed to it.

### bind()

Creates copy of whatever function being called on and whatever method is passed to it.

For a given function, creates a bound function that has the same body as the original function. The `this` object of the bound function is associated with the specified object, and has the specified initial parameters.

With the `bind()` method, an object can borrow a method from another object.

example:

```jsx
// The example below creates 2 objects (person and member).
// The member object borrows the `fullname` method from the person object:

const person = {
	firstName: "John",
	lastName: "Doe",
	fullName: function () {
		return this.firstName + " " + this.lastName;
	},
};

const member = {
	firstName: "Hege",
	lastName: "Nilsen",
};

// invoking method to the existing function object
let fullName = person.fullName.bind(member);
```

### call()

The **`call()`** method calls the function with a given `this` value and arguments provided individually.

example:

```jsx
function Product(name, price) {
	this.name = name;
	this.price = price;
}

function Food(name, price) {
	Product.call(this, name, price);
	this.category = "food";
}

console.log(new Food("cheese", 5).name);
// Expected output: "cheese"
```

### apply()

The **`apply()`** method calls the specified function with a given `this` value, and `arguments` provided as an array

example:

```jsx
const numbers = [5, 6, 2, 3, 7];
const max = Math.max.apply(null, numbers);
console.log(max);
// Expected output: 7

const min = Math.min.apply(null, numbers);
console.log(min);
// Expected output: 2
```

**Note:** This function is almost identical to `[call()](<https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Function/call>)`, except that the function arguments are passed to `call()` individually as a list, while for `apply()` they are combined in one object, typically an array — for example, `func.call(this, "eat", "bananas")` vs. `func.apply(this, ["eat", "bananas"])`.

### Function borrowing with apply

Is a way which allows functions to access the methods of the other objects.

Can be done using `apply` method.

example:

```jsx
var person1 = {
	firstName: "Jonh",
	lastName: "Doe",
	getFullName: function () {
		return this.firstName + " " + this.lastName;
	},
};

var person2 = {
	firstName: "Mike",
	lastName: "Scott",
};

// borrowing the "getFullName" method in person1 from person2
console.log(person1.getFullName.apply(person2));
```

### function currying with bind.

Is process of creating a new function from existing function with the default parameters.

Can be useful in mathematical use cases.

example:

```jsx
// function currying
function multiply(a, b) {
	return a * b;
}

// bind doesn't execute the function. It is permanently setting the value of parameters when copy is made

// will permanently set first paramter to 2
var multiplyByTwo = multiply.bind(this, 2);
// will permanently set first paramter to 3
var multiplyByThree = multiply.bind(this, 3);

// adding second paramters and printing the return statement
console.log(multiplyByTwo(4)); // output: 8
console.log(multiplyByThree(4)); // output: 12
```
