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

<details>
<summary>Question 7</summary>

Explain what pure functions are and some of their advantages.
<details>
<summary>Answer</summary>

In simple terms, a pure function is a function where the return value is only determined by its input values and that doesn’t have side effects such as the mutation of an object. This means that the function always returns the same result given the same arguments and that it doesn’t depend on a given application state that may change while the software is executed.

An example of a pure function is the test() function reported below. It declares two parameters, an array of numbers (array) and a number (max). The function returns true if the sum of the numbers of the array is less than the number; false otherwise.

```jsx
function test(array, max) {
   const sum = array.reduce((partial, number) => partial + number);
   return sum < max;
}
```

As you can see, the returned value of the test() function is only calculated on the basis of the provided arguments. Other examples of pure functions can be found in the JavaScript language itself. Some examples are Math.sin(), Math.max(), and Number.parseInt().

To give you a better understanding of what pure functions are, let’s see an example of an impure function:

```jsx
function sumRandom(number) {
   return Math.random() + number;
}
```

The `sumRandom()` function defined above is impure because its returned value depends on the random number calculated inside the function. So, even if we pass the same argument, at every call of the function the result will be different.

The main advantage of pure functions is their testability. Because the return value depends on arguments provided only, you don’t have to assume or mock any state of your software and you can focus on arguments and return values. Pure functions help you in writing predictable and deterministic code, which is easier to test.

Another advantage is that pure functions can be executed in parallel because they don’t have side effects, thus there is no chance they conflict with each other. Pure functions are also usually easier to understand and reuse because they don’t depend on a given state of the system nor they change the state of the application. Finally, results of pure functions can be cached for future reuse because the same input always yields the same output.

</details>
</details>

<details>
  <summary>Question 8</summary>
  
  <details> What is generator in JS? </details>
  
<details>
  <summary>Answer</summary>
  
  Generator are functions which can be exited and later re-entered. Their context (variable bindings) will be saved across re-entances. Generator functions are written using the 
  `function*` syntax. When called initially, generator functions do not executes any of their code, instead returning a type of iterator called a Generator. When a calue is consumed by calling the generator's `next` method, the Generator function executes until it encounters the `yield` keyword.
  
  The function can be called as many times as desired and returns a new Generator each time, however each Generator may only be itrated once.
  
  #### Example:
  
  A function that that generate unique identifiers
  
  ```jsx
  function * idCreator() {
  let i = 0;
  while (true) yield i++;
}

const ids = idCreator();

console.log(ids.next().value); // 0
console.log(ids.next().value); // 1
console.log(ids.next().value); // 2
  ```
  
  
  
</details>
  
</details>


### Computer Science Questions

<details>
  <summary>Question 1</summary>
  
  Implement an algorithm to determine if a string has all unique characters. You can not use any additonal data structures.
  Try to solve this question with better runtime than O(n^2) (naive solution)
  
  <details>
    <summary>Answer</summary>
    
```jsx
const hasUniqueCharacters = (string) => {
sortedChars = string.split("").sort();

for(const [index, letter] of sortedChars.entries()) {
  if(sortedChars[index + 1] && letter === sortedChars[index + 1]) {
    return false;
  }
}

return true;
}
```
    
Runtime complexity of this algorithm is O(n log n).
  </details>
</details>

<details>
  <summary>Question 2</summary>
  
  ***Palindrome Permutation:*** Given a string, write a function to check if it is a permutation of a palindrome. A palindrome is a word or phrase that is the same forwards and backwards. A permutation is a rearrangement of letters. The palindrome does not need to be limited to just dictionary words.

***EXAMPLE:***

Input: Tact Coa
Output: True (permutations: "taco cat", "atco eta", etc.)

  <details>
  <summary>Answer</summary>
  
  When we approach this question, we should ask ourself what does it mean that a given string is a palindrome? what can we learn from it? what features does a palindrome have?
  We can notice that every letter in a palindrome appears an even number of times in case the word's length is even, if it's length is odd - there will be a single letter that will appear odd number of times.
  Having noticing that, it is much easier now to code this problem. we will build a frequency dictionary, which will hold each letter frequency in the word.
  then, we will count how many odd frequencies there are - and if there are none (or one, if the word's length is odd) - its a palindrome permutation.
  
  ```jsx
  'use strict';

const buildFrequencyDict = (string) => {
  const frequencyDict = {};

  for(let letter of string) {
    let frequency = frequencyDict[letter]
    frequency ? frequencyDict[letter] = ++frequency : frequencyDict[letter] = 1;
  }

  return frequencyDict;
}

const isPalindromePermutation = (string = "tactcoapapa") => {
  const frequencyDict = buildFrequencyDict(string);

  let lettersWithOddFrequency = 0;
  for(const [letter, frequency] of Object.entries(frequencyDict)) {
    if(frequency % 2 !== 0) {
      lettersWithOddFrequency++;
    }
  }

  if(string.length % 2 !== 0) {
    lettersWithOddFrequency--;
  }

  return lettersWithOddFrequency === 0;
}
```

Runtime complexity of this algorithm is `O(n)`
  </details>
</details>

<details>
  <summary>Question 3</summary>
  
One Away: There are three types of edits that can be performed on strings: insert a character,
remove a character, or replace a character. Given two strings, write a function to check if they are
one edit (or zero edits) away. 

***EXAMPLE:***
<br> pale, ple -> true
<br> pales, pale -> true 
<br> pale, bale -> true 
<br> pale, bake -> false 
  <details>
  <summary>Answer</summary>
  
  Same as before, we want to find the characteristics of two words that are one edit away from one another.
  We can notice right away that in case of an update, the strings has equal length, and in the case of insertion or deletion, one word will be longer than the other by one character.
  Another thing we can notice, is that insertion and deletion are eventually the same thing - as they are inverse operations.
  
  In case of update - we'll go through one string letter by letter, and count how many letters are different from the matching letter in the other string.
  In case of insertion or deletion - we will go over the longer string, and on every iteration we will pick a letter discard from the word.
  
   ```jsx
  'use strict';

const isOneEditAway = (str1, str2) => {
  let lettersDiff = 0;
  for(const [index,letter] of str1.split("").entries()) {

    if(letter !== str2[index]) {
      lettersDiff++;
    }    
  }

  return lettersDiff <= 1
}

// Same logic applies to both insert and delete
const isOneInsertionAway = (str1, str2) => {
  const longerString = str1.length > str2.length ? str1 : str2;
    const shorterString = str1.length > str2.length ? str2 : str1;

    for(const index in longerString) {
      const stringWithoutCurrentLetter = longerString.slice(0, Number(index)).concat(longerString.slice(Number(index ) + 1))
      if(stringWithoutCurrentLetter === shorterString) {
        return true;
      }
    }

    return false;
}

const oneWay = (str1, str2) => {
  const lengthDiff = Math.abs(str1.length - str2.length);

  if(lengthDiff > 1) {
    return false;
  } else if(lengthDiff === 0) { 
    return isOneEditAway(str1, str2);
  } else { 
    return isOneInsertionAway(str1, str2)
  }

}
  ```
  
  Runtime complexity of this algorithm is `O(n)`.
  </details>
</details>

<details>
  <summary>Question 4</summary>
  
  String Rotation:Assumeyou have a method isSubstringwhich checks if oneword is a substring
of another. Given two strings, sl and s2, write code to check if s2 is a rotation of sl using only one
call to isSubstring (e.g., "waterbottle" is a rotation of "erbottlewat"). 

(If a string is a rotation of another, then it's a rotation at a particular point. For example,
a rotation of waterbottle at character 3 means cutting waterbottle at character 3
and putting the right half (erbottle) before the left half (wat))

  <details>
  <summary>Answer</summary>
  
  If a s2 is a rotation of s1, it means what there is a pivot point at s1, which divides to string to two. let's call them ***x*** and ***y***.
  if the left half of s1 is "wat", and the right one is "erbottle", we can denote it like this:
  <br>  `s1 = waterbottle = xy`
  <br> and s2 will be:
  <br> `s2 = erbottlewat = yx`
  
  <br> if we concatinate s2 to itself, we'll get:
  <br>  `s2s2 = erbottlewaterbottlewat = yxyx`
  
  and we can see that:
  <br>  `xy ⊆ yxyx`
  
  
  ```jsx
  // mimic `isSubstring` in JS
  const isSubstring = (string, subString) => {
  return string.includes(subString)
}

const isRotation = (s1, s2) => {
  return isSubstring((s2 + s2), s1)
}
  ```
  
  Runtime complexity of this algorithm is `O(n)`.
  </details>
</details>

<details>
  <summary>Question 5</summary>

Given an array of integers, return indices of the two numbers such that they add up to a specific target.

You may assume that each input would have exactly one solution, and you may not use the same element twice.

***Example:***
    Given nums = [2, 7, 11, 15], target = 9,

    Because nums[0] + nums[1] = 2 + 7 = 9,
    return [0, 1].
    
  <details>
  <summary>Answer</summary>
  
  ```jsx
  // two arrays traversal
const twoSumTwoPasses = function(nums, target) {

    const hashMap = {};

    for(const [index, number] of nums.entries()) {
      hashMap[number] = index;
    }
    
    for(const [index, number] of nums.entries()) {
      const compliment = target - number;

      if(hashMap[compliment]) {
        return [hashMap[compliment], index ]
      }
    }

    return "no match"
};

// one array traversal
const twoSumOnePass = function(nums, target) {

    const hashMap = {};
    
    for(const [index, number] of nums.entries()) {
      const compliment = target - number;

      if(hashMap[compliment] != undefined) {
        return [hashMap[compliment], index ]
      }

      hashMap[number] = index;
    }

    return "no match"
};
  ```
  </details>
</details>



### General Terms

<details>
  <summary>Question 1</summary>
  
  What does SOLID Stand for ? explain the basic idea
  
  <details>
    <summary>Answer</summary>
    `Single-responsibility principle`
        A class should only have a single responsibility, that is, only changes to one part of the software's specification should be able to affect the specification of the class.        
    ***Open–closed principle:***
        "Software entities ... should be open for extension, but closed for modification."
    *** Liskov substitution principle***
        "Objects in a program should be replaceable with instances of their subtypes without altering the correctness of that program." See also design by contract.
    ***Interface segregation principle***
        "Many client-specific interfaces are better than one general-purpose interface."
    ***Dependency inversion principle***
        One should "depend upon abstractions, [not] concretions."
  </details>
</details>