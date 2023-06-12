**# Day 12**

- [70. Learning from Other’s Good Code](#70-learning-from-others-good-code)
- [71. Deep Dive intoo Source Code: jQuery - Part 1](#71-deep-dive-intoo-source-code-jquery---part-1)
- [71. Deep Dive into Source Code: jQuery - Part 2](#71-deep-dive-into-source-code-jquery---part-2)
- [73. Deep Dive intoo Source Code: jQuery - Part 3](#73-deep-dive-intoo-source-code-jquery---part-3)
  - [Method chaining](#method-chaining)
  - [How jQuery is exposed for usage?](#how-jquery-is-exposed-for-usage)

## 70. Learning from Other’s Good Code

open source software are great source of good code form other people.

Learning from famous libraries will give good insight on writing quality codes and standard of the codes.

The most common source for the open source code is GitHub. Majority of open source soft wares, frameworks, and libraries repository can be found in GitHub.

For the course reference, we will look into JQuery.

## 71. Deep Dive intoo Source Code: jQuery - Part 1

jQuery is large source of JavaScript code.

Solves cross browser issues.

Mainly used to find the element and manipulate the DOM.

IIFE was used to check for the window property based on the environment it’s living.

jQuery itself is the function which accepts the selector and context. It’s just a function but not a function constructor.

Utilizes deep copy methods to extend properties and methods.

## 71. Deep Dive into Source Code: jQuery - Part 2

Has bunch of methods being used internally.

Uses sizzlejs which is CSS selector engine inside of the IIFE.

`$` in jQuery is just a function which looks into DOM which utilizes CSS selector to get the element and manipulate it.

## 73. Deep Dive intoo Source Code: jQuery - Part 3

### Method chaining

Calling one method after another, and each method affects the parent object.

### How jQuery is exposed for usage?

Goes through various checks like if window exists or not, If jQuery is already existing in global object and so on..

After checks and conditional verification, will return the jQuery object which will be then accessible from the global object.
