### Question #2

Implement a function called `createBase`, that will allow you to do the following:

```JavaScript
const addSix = createBase(6);
addSix(10); // returns 16
addSix(21); // returns 27
```

<details>
<summary>Answer</summary>
  
This question covers: [Closures](../../coding/javascript/closures.md)

You can create a closure to keep the value passed to the function `createBase` even after the inner function is returned. The inner function that is being returned is created within an outer function, making it a closure, and it has access to the variables within the outer function, in this case the variable baseNumber.

```JavaScript
function createBase(baseNumber) {
  return function(N) {
    // we are referencing baseNumber here even though it was declared
    // outside of this function. Closures allow us to do this in JavaScript
    return baseNumber + N;
  }
}

var addSix = createBase(6);
addSix(10);
addSix(21);
```

</details>

<br>

[Back To Index](../index.md)
