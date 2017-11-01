---
layout: post
title:  "Pass by Value and Pass by Reference in Javascript"
categories: [Javascript]
tags: javascript hackerblocks basics
vidId: B0C49q3sv4Y
img: 
---


Pass by Value and Pass by Reference in Javascript


Video Explanation by **Arnav Gupta**

A variable can be passed to the function in two ways. Either by value or by reference.

When we pass a variable by value to a function, a new copy of the variable is created
inside the function and all the changes to the variable are made to that copy of the variable.

When we pass a variable by reference to a function, the reference to that same variable is passed
to the function so any change in that variable is reflected back in the main function.

In javascript we can pass variables only by value to a function.

```js
function change_fruit(fruit){
    console.log("Original Value: " + fruit);        //Output: Original Value: Apple
    fruit="Mango"
    console.log("Modified Value: " + fruit);        //Output: Modified Value: Mango
}

var f="Apple"
console.log(f);     // Output: Apple
change_fruit(f);
console.log(f);     // Output: Apple
```

This means that the value of variable f is not changed. The change only took place in the
copy of the variable f that is variable fruit.

This is not the case when we pass non-primitive variables to a function. By non-primitives
we mean that the variable which are not numbers or strings or booleans. In case of non-primitives
the value of the variable is the reference to the non-primitive Object/value. So in this case,
passing the value means that the reference to the non-primitve is passed and hence changes are reflected back.
This is not a case of pass by reference. The variable is passed by value only.

```js
function change_numbers(arr){
    arr[0]=5;
    arr[1]=10;
}

var numbers = [1,2];
console.log(numbers);       // Output: [1, 2]
change_numbers(numbers);
console.log(numbers);       // Output: [5, 10]
```

So when we pass array numbers to the function, the reference to \[1,2\] is passed
to the function. Hence the changes are reflected back.
