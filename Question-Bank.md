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

this questions is about: [Closures](https://github.com/shaharhac/interview-prep/blob/master/JavaScript/closures.md), [IIFEs](https://github.com/shaharhac/interview-prep/blob/master/JavaScript/IIFE.md) 

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
