**# Day 27**

- [Section 6: Object Oriented Programming](#section-6-object-oriented-programming)
  - [108. Public vs Private](#108-public-vs-private)
  - [110. OOP in React.js](#110-oop-in-reactjs)

# Section 6: Object Oriented Programming

## 108. Public vs Private

In methods and properties starting with `-` are considered as private to distinguish but is not really.

From ES2022, we can have private classes in JavaScript.

to make private variable with ES2022, we can use `#` before property or method name.

The idea of public and private is still not well implemented in JavaScript.

example:

```jsx
class Employee {
	#name = "Test"; // private field
	setName(name) {
		this.#name = name;
	}
}
const emp = new Employee();
emp.#name = "New"; // error
emp.setName("New"); // ok

class Employee {
	#name = "Test";
	constructor(name) {
		this.#setName(name); // ok
	}
	#setName(name) {
		// Private method
		this.#name = name;
	}
}
const emp = new Employee("New"); // ok
emp.#setName("New"); // error
```

## 110. OOP in React.js

Is explanation of the class based react component usage.

example:

```jsx
class Toggle extends React.Component {
	// constructor()
	// other methods and properties

	render() {
		//	return the component
	}
}
```

Basically OOP is almost everywhere
