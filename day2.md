**# Day 2**

## Table of contents

- [Table of contents](#table-of-contents)
- [25. Conceptual Aside: Coercion](#25-conceptual-aside-coercion)
- [26. Comparison Operators](#26-comparison-operators)
- [28. Existence and Booleans](#28-existence-and-booleans)
- [29. Default Values](#29-default-values)
- [30. Framework Aside: Default Values](#30-framework-aside-default-values)
- [31. Objects and the Dot](#31-objects-and-the-dot)
- [32. Objects and Object Literals](#32-objects-and-object-literals)

## 25. Conceptual Aside: Coercion

Is the reason why I love Typescript xDD

Is process of converting a value from one type to another.

Is common in JavaScript as it’s dynamically typed language and is also a fundamental part of JavaScript.

example:

1. number + string will output string (number is coerced to string)
2. boolean + string will output string (boolean is coerced to string)
3. string + number will output number (string is coerced to number)

more examples and explaination can be found at: https://www.geeksforgeeks.org/what-is-type-coercion-in-javascript/

## 26. Comparison Operators

Is set of regular comparison operators.

While doing comparison, the coercion do occurs when different data types are compared.

note: numerical value of `null` is converted to `0` but it’s not evaluated as `0` at the time of comparison.

note: always prefer use `===` for comparison. which is strict equality check.

The `Object.is()` static method determines whether two values are the same value. It’s new method over the traditional comparison operators. ref: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/is

## 28. Existence and Booleans

whatever is put inside of `if()` it will convert it to boolean value. Which means the values and expressions are coerced into boolean.

## 29. Default Values

Can be used when expected values are not provided to the function while calling it.

It can be done by assigning value to the function parameter.

## 30. Framework Aside: Default Values

In case of the frameworks or libraries, where there could be possibility of same code to be existing with same value, OR operations are used to resolve the issue.

Following pattern is quite common to see in libraries or packages

```jsx
// if something is existing already in global scope then don't use.
window.librarayName = window.libraryName || "Lib 2";
```

## 31. Objects and the Dot

Object can have properties and methods.

It has reference to the location of it’s properties and methods.

dot after object name is used to access the properties and methods inside of it. It’s also called member access property.

example:

```jsx
// defining an object
const person = {
	firstName = "Alison"
	lastName = "Burger"
}

// accessing object properties with dot/member access property
console.log(person.firstName) // Alison
console.log(person.lastName) // Burger

// accessing object properties with key names
console.log(person["firstName"]) // Alison
console.log(person["lastName"]) // Burger
```

## 32. Objects and Object Literals

Objects can be created in multiple ways.

Object literal Is method to create a new object by simply declaring it with curly braces.

example: `let obj = { }`
