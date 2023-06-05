**# Day 4**

- [37. Conceptual Aside: By Value vs By Reference](#37-conceptual-aside-by-value-vs-by-reference)
  - [mutate](#mutate)
  - [call by values](#call-by-values)
  - [call by reference](#call-by-reference)
- [38. Objects, Functions, and this](#38-objects-functions-and-this)

## 37. Conceptual Aside: By Value vs By Reference

### mutate

means to change or update the value of the property.

### call by values

when a new value is assigned to a item, it will refer to the value of that item. It means, even if the assigned items value will be changed in future, the new item will still have the same value instead of the new one.

the values are assigned by value for primitive types

example:

```
let a = 3;
let b;
b = a; // will create separate space in memory for b
a = 5; // b will still be 3

```

### call by reference

when a new value is assigned to a item, it will refer to the location of that item. It means, if the assigned items value will be changed in future, the new item will also have the updated value.

non primitive (objects and functions) are assigned by reference

Even parameters are passed by references

example:

```
let obj1 = { greeting: "hi" }
let d;
d = obj1; // d will still hold the same value as obj1 even after upading it
obj1.greeting = "hellooo";

console.log(obj1.greeting); // "hellooo"
console.log(d.greting); // "hellooo"

```

## 38. Objects, Functions, and this

`this` points to global keyboard which is `window` in the browser.

Inside of the execution context of the function, it will still point to the global object.

When a function is attached to the object, `this` refers to the object that function is residing inside. Using it, the object structure can be modified.

Basically no programming language is perfect.
