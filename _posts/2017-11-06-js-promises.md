---
layout: post
title:  "Javascript Promises"
categories: [Javascript]
tags: javascript hackerblocks basics promises
vidId: U7ZzbNQPNB8
img: 
---


## Javascript Promises

We take a look at the ES6 promise API. We see the difference between the asynchronous functions using callback, and the new Promise syntax. The difference between resolve and reject is explained, and we also see how we can use a deffered resolve (handing the then() call after the promise has been resolved)

Video Explanation by **Arnav Gupta**

we have been writing asyncromous javascript code for quite a while now, but the thing about async code is it can easily become a asycn hell, sending callbacks inside callbacks can lead your code to be look somthing like this

```javascript
downloadFile("http://cb.lk/file.jpg", (err, data) => {
    if (!err) {
        encrypt(data, (err2, encData) => {
            if (!err2) {
                saveFile(encData, (err3, saved) => {
                    if (!err3 && saved) {
                        console.info("dl'ed, enc'ed and saved")
                    }
                })
            }
        } )
    }
})
```
To avoid this callback Hell, you can use javascript promises

```javascript
function downloadFile (url) {
    return new Promise(function (resolve, reject) {
        setTimeout(() => {
            if (url.startsWith("http")) {
                resolve("downloaded-data");
            } else {
                reject(new Error("link to thik thak do"))
            }
        }, 3000)
    })
}

downloadFile("cb.lk/file.txt")
    .then(function (data) {
        console.info(data)
    }).catch(function(err){
    	console.log(err)
    })
```
In the above code function `downloadFile` returns a `Promise`, which takes a function with 2 arguments  `resolve` and `reject`, `setTimeout` is a fake download method, so what your function intents to do goes here, if that function runs correctly call `resolve(arguments)` else call `reject(arguments)`.



when we call downloadFile("cb.lk/file.txt"), instead to passing callback as argument we can call `.then` and `.catch`, if `downloadFile` runs correctly, `.then` function will run and all the arguments passed in `resolve` will be available here as parameters and if it does not run correctly `.catch` is called with `reject` arguments.

with javascript promises you can chain the callbacks, one after other like fluent api, instead of passing callbacks, `.then` function will be called after resolving the previous and if any one of the `.then` function encounters an error, promise will call `.catch`, so you can have only one `.catch` for all the chained promises

```javascript
downloadFile("cb.lk/file.txt")
    .then(encrypt(data))
    .then(saveFile(data))
    .catch(function(err){
    // if either of encrypt or saveFile encounters an error, 
    // this catch block will be called and further then will not be called
    	console.log(err)
    })
```

with promises you can also resolve the result of `downloadFile("cb.lk/file.txt")` later at any time, this is called deffered resolve (handing the then() call after the promise has been resolved)

```javascript
let checkLater = downloadFile("cb.lk/file.txt");

// some other code here

checkLater.then(encrypt(data))
    .then(saveFile(data))
    .catch(function(err){
    // if either of encrypt or saveFile encounters an error, 
    // this catch block will be called and further then will not be called
    	console.log(err)
    })
```


## Promise.all([])

There is also an another function `Promise.all([])` which takes an array of promises, and gives an array of result of that promises.

```javascript

Promise.all([
    downloadFile('http://cb.lk/logo.png'),
    downloadFile('http://cb.lk/banner.png'),
    downloadFile('http://cb.lk/promo.png')
]).then(function(data){
	// data here is an array of result of all the promises
    console.log(data)
}).catch(function(err){
	// if any one of the promises gives an error,
    // this .catch is called and further promises will not be called
    console.log(err)
})
```
###

Promises were introduced in ES6, earlier promises could be used in javascript by using [Bluebird](http://bluebirdjs.com/docs/getting-started.html). you can read more on promises on the [mdn docs](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise)







