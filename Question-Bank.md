## Questions

### JavaScript Questions
<details>
<summary>Question 1</summary>

What will the following code output?

```
for (var i = 0; i < 3; i++) {
  setTimeout(function() { alert(i); }, 1000 + i);
}
```

<details>
<summary>Answer</summary>

this question is about: [Closures](https://github.com/shaharhac/interview-prep/blob/master/JavaScript/closures.md), [IIFEs](https://github.com/shaharhac/interview-prep/blob/master/JavaScript/IIFE.md) 

The goal of the code above is to alert the numbers 0, 1, and 2 each after 1, 1.1, and 1.2 seconds, respectively. The problem though, is that if you run the above code in your console, you actually get the number 3 alerted 3 times after 1, 1.1, and 1.2 seconds.

A JavaScript closure is when an inner function has access to its outer enclosing function's variables and properties. In the code above, the following line of code:
```
setTimeout(function() { alert(i); }, 1000 + i);
```
uses a variable i which is declared outside of itself. The variable i is actually declared within the for loop and the inner function accesses it. So when the for loop is done running, each of the inner functions refers to the same variable i, which at the end of the loop is equal to 3.
</details>


<details>
<summary>Follow-up Questions</summary>

Correct the for loop above, so that the numbers will be console logged in the right order

<details>
<summary>Answer</summary>

Our goal is for each inner function to maintain its reference to the variable i without the value of it being altered. We'll solve this using an IIFE

```
for (var i = 0; i < 3; i++) {
  setTimeout(function(i_local) { 
    return function() { alert(i_local); } 
  }(i), 1000 + i);
}
```
We pass the variable i into the outer function as a local variable named i_local, where we then return a function that will alert the i_local for us. This should now correctly alert the numbers 0, 1, and 2 in the correct order.

</details>

</details>

</details>


<details>
<summary>Question 2</summary>
  
Write a function that would allow you to do this.
```
 var addSix = createBase(6);
addSix(10); // returns 16
addSix(21); // returns 27
```

<details>
<summary>Answer</summary>
  
this question is about: [Closures](https://github.com/shaharhac/interview-prep/blob/master/JavaScript/closures.md)

You can create a closure to keep the value passed to the function createBase even after the inner function is returned. The inner function that is being returned is created within an outer function, making it a closure, and it has access to the variables within the outer function, in this case the variable baseNumber.

```
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
</details>

<details>
<summary>Question 3</summary>
  
How would you use a closure to create a private counter?

<details>
<summary>Answer</summary>
  
this question is about: [Closures](https://github.com/shaharhac/interview-prep/blob/master/JavaScript/closures.md)

You can create a function within an outer function (a closure) that allows you to update a private variable but the variable wouldn't be accessible from outside the function without the use of a helper function.

```
function counter() {
  var _counter = 0;
  // return an object with several functions that allow you
  // to modify the private _counter variable
  return {
    add: function(increment) { _counter += increment; },
    retrieve: function() { return 'The counter is currently at: ' + _counter; }
  }
}

// error if we try to access the private variable like below
// _counter;

// usage of our counter function
var c = counter();
c.add(5); 
c.add(9); 

// now we can access the private variable in the following way
c.retrieve(); // => The counter is currently at: 14
```

</details>
</details>

<details>
<summary>Question 4</summary>
  
What do the following lines output, and why?

```
console.log(1 < 2 < 3);
console.log(3 > 2 > 1);
```

<details>
<summary>Answer</summary>
  
The first statement returns true which is as expected.

The second returns false because of how the engine works regarding operator associativity for < and >. It compares left to right, so 3 > 2 > 1 JavaScript translates to true > 1. true has value 1, so it then compares 1 > 1, which is false.

</details>
</details>

<details>
  <summary>Question 5</summary>
  
  What will be printed to the console?
  
  ```jsx
  function foo() {
   var a = 1;
   const b = 2;
   let c = 3;
 
   if (b < 10) {
      var a = 10;
      const b = 11;
      let c = 12;
 
      console.log(a, b, c);
   }
 
   console.log(a, b, c);
 
   console.log(d, e);
 
   var d = 4;
   const e = 5;
}
 
foo();
  ```
  
  <details>
  <summary>Answer</summary>
  
  this question is about: [Variables](https://github.com/shaharhac/interview-prep/blob/master/JavaScript/variables.md), 
  
  ```
  10 11 12
  10 2 3
  Uncaught ReferenceError: e is not defined
  ```
  </details>
</details>

<details>
  <summary>Question 6</summary>
  
  What’s the difference between `bind()`, `call()`, and `apply()`?
  <details>
    <summary>Answer</summary>
  
  #### bind
  The `bind()` method creates a new function that, when called, has its `this` keyword set to the provided value, with a given sequence of arguments preceding any provided when the new function is called.
  
    
  for example:
  ```jsx
  const module = {
  x: 42,
  getX: function() {
    return this.x;
  }
};

const unboundGetX = module.getX;
console.log(unboundGetX()); // The function gets invoked at the global scope
// expected output: undefined

const boundGetX = unboundGetX.bind(module);
console.log(boundGetX());
// expected output: 42

  ```
  
  
  The `apply()` method is identical to `call()`, except `apply()` requires an array as the second parameter. The array represents the arguments for the target method.
  #### call
  The `call()` method calls a function with a given this value and arguments provided individually.
  
  ```jsx
  function Product(name, price) {
  this.name = name;
  this.price = price;
}

function Food(name, price) {
  Product.call(this, name, price);
  this.category = 'food';
}

console.log(new Food('cheese', 5).name);
// expected output: "cheese"

  ```
  
  #### apply
  The `apply()` method calls a function with a given this value, and arguments provided as an array
  
  ```jsx
  const numbers = [5, 6, 2, 3, 7];

const max = Math.max.apply(null, numbers);

console.log(max);
// expected output: 7

const min = Math.min.apply(null, numbers);

console.log(min);
// expected output: 2

  ```
  </details>
</details>
