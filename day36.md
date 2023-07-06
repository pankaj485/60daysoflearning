**# Day 36**

- [Section 10: Modules In JavaScript](#section-10-modules-in-javascript)
  - [Section Overview](#section-overview)
  - [150. What Is A module?](#150-what-is-a-module)
  - [151. Module Pattern](#151-module-pattern)
  - [152. Module Pattern Pros and Cons](#152-module-pattern-pros-and-cons)
    - [Pros](#pros)
    - [Cons](#cons)
  - [153. CommonJs, AMD, UMD](#153-commonjs-amd-umd)
    - [CommonJS](#commonjs)
    - [AMD](#amd)
    - [UMD](#umd)
  - [154. ES6 Modules](#154-es6-modules)
  - [155. Section Review](#155-section-review)

# Section 10: Modules In JavaScript

## Section Overview

Will learn:

1. Native ES Modules
2. CommonJS
3. UMD
4. AMD
5. IIFE

Learn to make the code more modular.

## 150. What Is A module?

Allows to structure the code base in modular way to share the data back and forth.

Larger application relies on module based architecture to build to make the project more modular and less buggy.

JavaScript has ES module system.

## 151. Module Pattern

Was used in the initial days of JavaScript.

With module pattern, we can make the variables and properties to be scoped within particular module only which won’t affect the global scope and the functions within the modules can still access the variables and properties.

Allows to use a function as a module. Whatever is returned with the function can be used by other functions.

## 152. Module Pattern Pros and Cons

### Pros

Allows richer maintainability by allowing particular variables only to be exported.

Lowers the dependency by utilizing the local scope.

Updating a single module is easier if the module is decoupled from the other modules.

### Cons

The module exports will still pollute the global scope and can still be overwritten.

The order of the script imports matters as the change of variables to be overwritten is high. It can also affect the parameters imported on the modules dependent to other modules.

## 153. CommonJs, AMD, UMD

### CommonJS

CommonJs and AMD are the new module patterns used over the module pattern.

The CommonJS pattern is mainly used for servers an hence were heavily used with NodeJs.

Unlike the module pattern, it’s not order dependent and is not synchronously imported which means it won’t hang on until one module is completely imported.

Module bundlers like webpack allows the multiple JavaScript files into a single file.

example:

```jsx
// example: importing module with CommonJS standard
const greeter = require("./greeter/greeter");

const sampleModule = function () {
	let returnValue = {
		greeting: "hello",
		localtion: "bengaluru",
	};
};

// example: exporting module
module.exports = { sampleModule };
```

### AMD

Was designed specifically for browsers.

Loads scripts or modules asynchronously as needed and is crucial for browsers.

Both solves the problem of pollution of the global scope and dependency resolution.

### UMD

Is universal module bundler.

Is a basic way to decide which to use AMD or CommonJS which tried to solve the problem lacking between two.

Isn’t heavily used at all.

JavaScript now already has native module system called ES6 modules.

## 154. ES6 Modules

Is native to JavaScript

With ES6 modules, the script has to be defined as type module to be utilized and has to be served with server.

example:

```jsx
<script type="module">import sampleModule from "./greeter/greeter"</script>
```

example:

Import and export with ES6 modules.

```jsx
// example: importing module with ES6 standard
import greeter from "./greeter/greeter";

// example: exporting module with ES6 standard (named export)
export function sampleModule() {
	let returnValue = {
		greeting: "hello",
		localtion: "bengaluru",
	};
}
```

default Import and export with ES6 modules

```jsx
// importing default and named exports from ES6 modules
import giveGreets, { sampleModule } from "./greeter/greeter";

// example: default export wih ES6 module
export default function giveGreets() {
	return {
		first: "hello",
		second: "hi",
		third: "supp",
	};
}
```

## 155. Section Review

Learned about the modules, their concepts and understood what problems they are actually solving.
