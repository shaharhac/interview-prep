### Question #3

Given an array of integers, return indices of the two numbers such that they add up to a specific target.

You may assume that each input would have exactly one solution, and you may not use the same element twice.

**Example:**

Given nums = [2, 7, 11, 15], target = 9,

Because nums[0] + nums[1] = 2 + 7 = 9,
return [0, 1].

<details>
<summary>Answer</summary>

```JavaScript
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

Runtime complexity of this algorithm is `O(n)`.

</details>

<br>

[Back To Index](../index.md)
