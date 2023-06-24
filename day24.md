**# Day 24**

- [Section 5: The 2 Pillars: Closures and Prototypal Inheritance](#section-5-the-2-pillars-closures-and-prototypal-inheritance)
  - [84. Prototypal Inheritance](#84-prototypal-inheritance)
    - [Inheritance](#inheritance)
  - [85. Prototypal Inheritance 2](#85-prototypal-inheritance-2)
    - [Inheriting from one object to another:](#inheriting-from-one-object-to-another)
  - [86. Prototypal Inheritance 3](#86-prototypal-inheritance-3)
  - [88. Prototypal Inheritance 5](#88-prototypal-inheritance-5)
  - [89. Prototypal Inheritance 6](#89-prototypal-inheritance-6)
    - [Constructor functions](#constructor-functions)
- [Section 6: Object Oriented Programming](#section-6-object-oriented-programming)
  - [95. Section Overview](#95-section-overview)
  - [96. OOP and FP](#96-oop-and-fp)
  - [97. OOP Introduction](#97-oop-introduction)

# Section 5: The 2 Pillars: Closures and Prototypal Inheritance

## 84. Prototypal Inheritance

### Inheritance

Is when an object get access to methods and properties of another object.

Since array and functions are special objects only, they also get access to the regular object methods.

To access the base object methods, `__proto__` is used. It is possible due to prototype chain.

There is no class in JavaScript, it’s prototypal inheritance all over.

It allows to use only one instance of memory space which saves memory and also solves non required complexities.

## 85. Prototypal Inheritance 2

### Inheriting from one object to another:

To inherit properties and methods to an object from an object, assign the `__proto__` the object to inherit to object to inherit from.

syntax: `object1.__proto__ = object2`

If there will be overlapping methods and properties in the inheriting object then it will override the methods and properties which are inherited.

The prototype chain can be verified with `isPrototypeOf` method.

syntax: `object1.isPrototypeOf(object2)`

## 86. Prototypal Inheritance 3

To check a property is part of an object, `hasOwnProperty` method can be used.

syntax: `object.hasOwnProperty()`

Note: scope chain and prototype chain are not same

Note: `__proto__` is not advised to be used as it causes performance issues.

`__proto__` points up to the prototype chain which lives on the prototype itself.

## 88. Prototypal Inheritance 5

using `__proto__` isn’t advised as it causes performance issues.

Instead of it, we can use `Object.create(baseObjectName)`

## 89. Prototypal Inheritance 6

Only functions have the `prototype` property in JavaScript. It gets created when functions are created.

Prototypes are used only with constructor functions.

### Constructor functions

Starts with capita letter and contains actual blueprint of the function we will be using.

All functions prototypes are having prototype function. which is `Function.prototype`

typeof object is function because it has prototype property. Because it has the `Object` constructor. In order to create an object, JavaScript has to utilize the constructor functions.

Saying that, the typeof `Object` constructor functions itself however is of object type as it’s a special function.

# Section 6: Object Oriented Programming

## 95. Section Overview

how oops makes easier to extend, maintain, make memory efficient and dry applicable code.

OOP and FP best practices

## 96. OOP and FP

OOP says to have all the data and the functions in a single place. while FP says to separate the data and functions in separate place.

JavaScript allows to use both of the concepts based on the problems and pick the right paradigm.

## 97. OOP Introduction

Is very common style of programming.

Models real world models. Contains data and methods in a single place.

Programming languages are either class based or prototype based.
