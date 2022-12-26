
# Async Programming


## Promises
Promises are one way to handle asynchronous operations in JavaScript. Each promise represents a single operation.
It’s made to solve the problem of combining multiple pieces of asynchronous code in a clean way.
With promises, we can avoid nesting callbacks too deeply.

Promises have 3 states. They can be **pending**, which means the outcome isn’t known yet since the operation hasn’t start yet.
It can be **fulfilled**, which means that the asynchronous operation is successful and we have the result.
It can also be **rejected**, which means that it failed and has a reason for why it failed.
A promise can be settled, which means that it’s either fulfilled or rejected.
![promises](https://miro.medium.com/max/1400/1*0mBlni5vsYZE2wFzfVv8EA.png)
## async/await

async/await is a new way to write promise chains in a shorter way.
async functions return a promise. await is always for a single Promise.
<br/>
await only blocks the code execution within the async function. It only makes sure that the next line is executed when the promise resolves. So, if an asynchronous activity has already started, await will not have any effect on it.
<br/>

### When to use What? 
1. If the output of function2 is dependent on the output of function1, I use `await`.
2. If two functions can be run in parallel, create two different `async` functions and then run them in parallel.
3. To run promises in parallel, create an array of promises and then use `Promise.all(promisesArray)`
4. Instead of creating huge async functions with many `await asyncFunction()` in it, it is better to create smaller async functions. This way, we will be aware of not writing too much blocking code.
