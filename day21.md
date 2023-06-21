**# Day 21**

- [Section 4: Types in JavaScript](#section-4-types-in-javascript)
  - [57. JavaScript Types](#57-javascript-types)
    - [undefined vs null](#undefined-vs-null)
    - [primitive and non-primitive types](#primitive-and-non-primitive-types)
  - [58. Array.isArray()](#58-arrayisarray)
  - [58. Pass by Value vs Pass By Reference](#58-pass-by-value-vs-pass-by-reference)

# Section 4: Types in JavaScript

## 57. JavaScript Types

JavaScript has following types:

1. number
2. boolean
3. string
4. undefined
5. null
6. symbol
7. objects

type of null is object in JavaScript and is a bug

Symbol is new type introduced in ES6. It helps to identify the object properties.

Arrays and functions are objects in JavaScript.

### undefined vs null

undefined absence of definition while null is absence of value

### primitive and non-primitive types

all types related to object is non-primitives and other than the object types are primitives.

primitive is data types which represents single data. It directly contains value of a particular type.

non-primitive doesn’t contain a value directly but is referenced to the memory.

primitives in JavaScript has object wrappers. example: `Boolean(true).toString()`

## 58. Array.isArray()

Array are special objects in JavaScript.

`.isArray()` is method to validate whether that item is an Array or not.

## 58. Pass by Value vs Pass By Reference

Pass by values means the value is directly used and passed which is mainly utilized in the primitive data types while pass by reference means the address in memory is passed which is mainly utilized in non-primitive data types.

Objects values are not directly passed but the reference to that memory location is passed. It will cause the modification of the value by other instance of the copies too.

example:

```jsx
let obj1 = { name: "Yao", password: "123" };
let obj2 = obj1;

obj2.password = "hellooooo"; // changes value in the memory

console.log(obj1); // { name: 'Yao', password: 'hellooooo' }
console.log(obj2); // { name: 'Yao', password: 'hellooooo' }
```

To prevent it, use `Object.assign()` or spread operator. These will shallow clone the object.

shallow clone: only first level of object is copied and any other nested objects will be still passed by reference

example:

using spread operator

```jsx
let obj1 = { name: "Yao", password: "123" };
let obj2 = { ...obj1 };

obj2.password = "hellooooo";

console.log(obj1); // { name: 'Yao', password: '123' }
console.log(obj2); // { name: 'Yao', password: 'hellooooo' }
```

using `Object.assign()`

```jsx
let obj1 = { name: "Yao", password: "123" };
let obj2 = Object.assign({}, obj1);

obj2.password = "hellooooo";

console.log(obj1); // { name: 'Yao', password: '123' }
console.log(obj2); // { name: 'Yao', password: 'hellooooo'
```

To prevent shallow cloning, use deep cloning which includes the process of stringifying the whole object and again parsing it back to JSON and then assigning it.

Deep cloning has performance implications in case of deeply nested objects.

example: `let deepClone = JSON.parse(JSON.stringify(obj));`
