---
layout: post
title:  "Javascript Closures"
categories: javascript
src: https://www.youtube.com/embed/kPPy-VwuLxc
img:
---
Javascript is one of the many languages that support 'closure' scopes.

Let us take a normal piece of JS code -

```js
function myFun () {
    var myVar = "some value";
}

myFun();

console.log(myVar); //undefined
```

When we run it, ovbiously, we would get an error on the last line because
myVar is not present in the scope anymore, as we are outside the function.

Now consider this piece of code

```js
function funcGen () {
    var someVal = 10;
    function aFun () {
        someVal++;
        return someVal
    }

    return aFun
}

var myFun = funcGen();

console.log(myFun()); //11
console.log(myFun()); //12
```

In this example, we are creating a new function inside `funcGen` and returning it.
When we do that. The returned value is a function `myFun` which itself can be called
like we have done in the last line.

When we do that, we will see that `11` and `12` are printed (doing ++ on 10 twice)
When we are on the last two lines, `funcGen` scope has ended, and hence we should
not be able to access `someVal`, but we are able to, because of **_closure_**.

The function `aFun`, since it is created inside `funcGen` gets access to all
local variables of `funcGen` and continues to have access to them after the
scope of `funcGen` has ended. This scope that a function inherits from the parent
function is called a _**closure scope**_.




