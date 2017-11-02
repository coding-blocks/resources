---
layout: post
title:  "var, let and const in Javascript"
categories: [Javascript]
tags: javascript hackerblocks basics
vidId: nmwEG_fpZlk
img: 
---


var, let and const in Javascript


Video Explanation by **Arnav Gupta**

With the coming of ECMAScript 2015,
we have two new keywords to declare the variables - let and const.

var keyword is used to declare variable having functional scope.

let keyword is used to declare variables having block scope.

const keyword is used to declare variable having block scope and which are constant. Constant here does not means that the value
it holds is immutable. Constant here means that the variable can not be reassigned to some other value. One more important thing
to remember is that we have to provide the initial value to the variable at the time of declaration of the variable.

variables declared with let and const can not be referenced before their initialization is encountered at runtime unlike variables
declared with var keyword which gets hoisted at the top of the function.

```js
console.log(word);      // Output: undefined

var word="Hello";

console.log(word);      // Output: Hello
```

```js
console.log(word);      // Output: Reference Error

let word="Hello";

console.log(word);
```

```js
console.log(word);      // Output: Reference Error

const word="Hello";

console.log(word);
```

One more important thing we need to see is that the value of a variable declared with const keyword can not be reassigned but the value
itself can change. For eg

```js
const obj = { p: 10, q: 20};

obj = {a: 10} // Asignment to constant variable Error

obj.p = 200; // Allowed, value of key changed

obj.r = 30; // Allowed, New key added
```