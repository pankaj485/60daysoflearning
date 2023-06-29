**# Day 29**

- [Section 7: Functional Programming](#section-7-functional-programming)
  - [115. Functional Programming Introduction](#115-functional-programming-introduction)
  - [116. Exercise: Amazon](#116-exercise-amazon)
  - [117. Pure Functions](#117-pure-functions)
  - [118. Pure Functions 2](#118-pure-functions-2)

# Section 7: Functional Programming

## 115. Functional Programming Introduction

Is all about separation of concerns.

It also separates data and functions unlike in OOP.

Operates on well defined data structures like Array and Objects.

The goal of the functional programming is also same as OOP which is to make code:

1. Clear + Understandable
2. Easy to extend
3. Easy to maintain
4. Memory efficient
5. DRY

Everything boils down to pure functions. There will be separation between data and the behavior of the program.

All objects created in functional programming are immutable(once something is created, it can’t be changed)

Has many restrains which allows to make sure code doesn't go out of a hand.

## 116. Exercise: Amazon

challenge: https://replit.com/@aneagoie/FP#index.js

code:

```jsx
// Amazon shopping
const user = {
	name: "Kim",
	active: true,
	cart: [],
	purchases: [],
};

const orderedItem = {
	item: "Apple juice",
	price: 20,
};

//Implement a cart feature:
// 1. Add items to cart.
function addToCart(itemDetail, userDetail) {
	let { item, price } = itemDetail;
	const { name } = userDetail;
	// 2. Add 3% tax to item in cart
	itemDetail.price = price + 0.03 * price;

	userDetail.cart.push(itemDetail);
	console.log(`${item} is added to ${name}'s account.`);
	console.log(user);
}

// 3. Buy item: cart --> purchases
function purchaseItem(itemDetail, userDetail) {
	let { item } = itemDetail;
	const { name } = userDetail;

	userDetail.purchases.push(itemDetail);
	console.log(`${item} is added to purchase list of ${name}.`);
	console.log(user);
}

// 4. Empty cart
function emptyCart(userDetail) {
	const { name } = userDetail;

	userDetail.cart = [];
	console.log(`${name}'s cart is cleared.`);
	console.log(user);
}

addToCart(orderedItem, user);
purchaseItem(orderedItem, user);
emptyCart(user);

//Bonus:
// accept refunds.
// Track user history.
```

## 117. Pure Functions

There are 2 fundamental rules of pure functions:

1. A pure function has to return same output given the same input (should give same output every time executed given the same parameters)
2. The pure function can’t modify anything outside itself(shouldn’t have side effects).

## 118. Pure Functions 2

Pure functions avoids many bugs as it has it’s own block and it won’t allow mutations and can’t modify the values outside of it’s block.
