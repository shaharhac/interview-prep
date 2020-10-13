
# Async Programming


## Promises
Promises are one way to handle asynchronous operations in JavaScript. Each promise represents a single operation.
It’s made to solve the problem of combining multiple pieces of asynchronous code in a clean way.
With promises, we can avoid nesting callbacks too deeply.

Promises have 3 states. They can be **pending**, which means the outcome isn’t known yet since the operation hasn’t start yet.
It can be **fulfilled**, which means that the asynchronous operation is successful and we have the result.
It can also be **rejected**, which means that it failed and has a reason for why it failed.
A promise can be settled, which means that it’s either fulfilled or rejected.
