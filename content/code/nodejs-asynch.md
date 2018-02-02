+++
title = "Node.js callbacks, promises, asynch/awaits"
date = "2018-02-01T20:04:42-08:00"
draft = false

+++

### Callback Hell

So what is callback hell?

Well, in JavaScript, it is really the only way to write code for having functionality attached or run after events. Think about the browser, we can't write block I/O code on the browser now can we?

So JS uses callbacks, and in JS they run into something called callback hell. THis is where all these function callbacks chain together and look like a mess. 

Now I am working with Node.js. Node has something called promises, which help with giving an order of execution for this asynchronous code and making it more readable.

Here is an example:

```javascript
const myPromise = new Promise(function(resolve, reject) {
  
  // code here
  
  if (codeIsFine) {
    resolve('fine')
  } else {
    reject('error')
  }
})
myPromise
  .then(function whenOk(response) {
    console.log(response)
    return response
  })
  .catch(function notOk(err) {
    console.error(err)
  })
```

Deconstructing it:
* The promise is made with a function with `resolve` and `reject` as arguments
* When your code comes back with a success, go down the `resolve` path, otherwise `reject`
* When `resolve` is found in `.then`, the code executes for that promise
* Same is said for `reject` for `.catch`

Pretty readable eh? 

The Javascript callbacks can look even better with `async` and `await`

### Asynch/Await

Ths method is like decorating promises with making your own callbacks

You just have to prepend your functions with the `async` keyword

The part using the `async` function will have to `await` for it to finish

Here:
```javascript

sumTwentyAfterTwoSeconds(10)
  .then(result => console.log('after 2 seconds', result))

async function sumTwentyAfterTwoSeconds(value) {
  const remainder = afterTwoSeconds(20)
  return value + await remainder
}

function afterTwoSeconds(value) {
  return new Promise(resolve => {
    setTimeout(() => { resolve(value) }, 2000);
  });
}
```
* sumTwentyAfterTwoSeconds is an asynch function
* Our code waits for the resolve, reject of the sumTwentyAfterTwoSeconds promise
* at the `.then` and `await` it finishes and executes `afterTwoSeconds(20)` and returns value + remainer

