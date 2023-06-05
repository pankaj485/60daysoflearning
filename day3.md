**# Day 3**

- [33. Framework Aside: Faking Namespaces](#33-framework-aside-faking-namespaces)
  - [namespace](#namespace)
- [34. JSON and Object Literals](#34-json-and-object-literals)
- [35. Functions are Objects](#35-functions-are-objects)
  - [First class objects](#first-class-objects)
- [36. Function Statements and Function Expressions](#36-function-statements-and-function-expressions)
  - [Expression](#expression)
  - [statement](#statement)

## 33. Framework Aside: Faking Namespaces

### namespace

Is a container for variables and functions with same name separate.

Example: two difference objects can have same variables but they are not linked to each other as they are name spaced to their own parent objects.

## 34. JSON and Object Literals

Is inspired by Objects but is not same

Is the format of data

keys and values are warped inside of quotes `"` separated by colon `:`

Has stricter rules compared to objects.

## 35. Functions are Objects

### First class objects

Functions are special type of object. It has all the features of normal object and some additional hidden properties.

Everything that can be done with the other types, can be done with the functions. It can be assigned to variables, passed as an argument, created on the fly.

A function can be anonymous in js (not having a name).

Functions are invocable and can be passed to other properties like primitive types. It has 2 properties:

1. Name (name of the function)
2. Code (body of the function)

Just like for objects, we can add properties to the functions.

example:

```
// function declaration
function greet(){
	console.log("hello there");
}

// adding properties
greet.language = "english";

// accessing the added property
console.log(greet.language); // that's how it's an object

```

more on first class functions: https://developer.mozilla.org/en-US/docs/Glossary/First-class_Function

## 36. Function Statements and Function Expressions

### Expression

Is a unit of code that results in a value. It doesn’t have to be saved to a variable. example: `1 + 2` will return `3`

### statement

statement doesn’t return the values but does the work only. example: if block doesn’t return anything but the condition inside of it is expression which results in boolean value

Function expression is when it results in some value when executed and statement is when it doesn’t

example:

```
// function statement
// when the function executes, it simply executes and doesn't do aything in execution phase
fuction greet(){
	console.log("hi");
}

// function expression
// when the function executes, it will results in returning the object which makes it function expression.
let greetFunction = function(){
	console.log("hi")
}

```

Note: function statements are hoisted but not the expressions. Which will result in undefined is not function error if it’s accessed before it’s invoked (executed).
