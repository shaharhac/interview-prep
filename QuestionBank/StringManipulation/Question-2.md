### Question #2

**Palindrome Permutation:** Given a string, write a function to check if it is a permutation of a palindrome. A palindrome is a word or phrase that is the same forwards and backwards. A permutation is a rearrangement of letters. The palindrome does not need to be limited to just dictionary words.

**example**:

**input**: Tact Coa

**output**: True (permutations: "taco cat", "atco eta", etc.)

<details>
<summary>Answer</summary>

When we approach this question, we should ask ourself what does it mean that a given string is a palindrome? what can we learn from it? what features does a palindrome have?
We can notice that every letter in a palindrome appears an even number of times in case the word's length is even, if it's length is odd - there will be a single letter that will appear odd number of times.
Having noticing that, it is much easier now to code this problem. we will build a frequency dictionary, which will hold each letter frequency in the word.
then, we will count how many odd frequencies there are - and if there are none (or one, if the word's length is odd) - its a palindrome permutation.

```JavaScript

const buildFrequencyDict = (string) => {
    const frequencyDict = {};

    for(let letter of string) {
        let frequency = frequencyDict[letter];
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

<br>

[Back To Index](../index.md)
