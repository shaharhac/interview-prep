# Arrays and Strings

## Questions

<details>
  <summary>Question 1</summary>
  
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
  <summary>Question 2</summary>
  
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

arrays and strings are fairly straightgforward, so there is no need to elborate on this.
having said that, arrays and strings interview questions often aren't that simple. you should be familiar with some concepts that will improve you code runtime complexity.

## Hash Table

A hash table is a data structure that maps kets to values for highly efficient lookup.
originally, the implementation uses an array of linked lists and a hash code function.
to insert a key-value pair:
1. compute the key's hash code (two different keys could have the same hash code - there are infinite number of keys and finite number of ints)
2. map the hash code to an index in the array (there are many ways to do this, often we do it with `hash(key) % array.length`)
3. at this index, there is a linked list of keys and values. Store the key and value in this index. We use a linked list beacuse of collisions: you could have two different keys with the same hash code, or two different hash codes that map to the same index

To retrieve the value pair by its key, you repeat this process. Compute the hash code from the key, and then compute the index from the hash code. Then seatch through the linked list for the value with this key.

let's talk about runtime complexity - at the worst case you could have a huge amount of collisions, which leads the runtime to be `O(n)`, where ***N*** is the number of keys.
however, we generally assume a good implementation that keeps collisions to a minimum, in which case the lookup time is `O(1)`.




in JavaScript, we don't really need this implementation of hash map, because we can use a simple object (Map is also an option).
