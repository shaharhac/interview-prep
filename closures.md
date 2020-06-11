## Closures

try to answer the questions below first, then read the rest of the page

<details>
  <summary>What is a closure</summary>
  Closure - inner function has access to variables and parametes of its outer function (even after the outer function has returned).
</details>
<details>
  <summary>State two closures use cases</summary>
  
  * Data Privacy (counter example from below)
  * Function Factory (makeAdder for example)
</details>



A closure gives you access to an outer function’s scope from an inner function. The inner function will have access to the variables (and parametres) in the outer function scope, even after the outer function has returned.

To use a closure, we need to define a function inside another function and "expose" it - to "expose" a function, return it or pass to another function.

### Example

```
function makeAdder(x) {
  return function(y) {
    return x + y;
  };
}

var add5 = makeAdder(5);
var add10 = makeAdder(10);

console.log(add5(2));  // 7
console.log(add10(2)); // 12
```
In this example, we have defined a function makeAdder(x), that takes a single argument x, and returns a new function. The function it returns takes a single argument y, and returns the sum of x and y.

### Data Privacy
Closures can be useful to create private variables inside a function. the private variables are only in the outer function, and one can reach the data only from the inner function

```
function makeCounter() {
    let counter = 0;
    function inc() {
        return ++counter
    }
    function dec() {
        return --counter
    }
    function print(){
        console.log(counter)
    }
    return {inc,dec,print}
}

let counter1 = makeCounter();
let counter2 = makeCoutner();

counter1.inc()
counter1.inc()
counter1.inc()

counter2.dec()
counter2.dec()

coutner1.print() // logs 3
coutner2.print() // logs -2
```
