# Time Complexity

Try to answer this questions first, then continue reading

<details>
  <summary>what is the time complexity of Binary Search?</summary>
  
  O(log n)
</details>
<details>
  <summary>What is the time complexity of Linear Search?</summary>
  
  O(n)
</details>
<details>
  <summary>What is the time complexity of Quick Sort?</summary>
  
  O(n * log n)
</details>
<details>
  <summary>What is the time complexity of Selection Sort?</summary>
  
  O(n * n)
</details>
<details>
  <summary>What is the time complexity of Traveling salesperson problem?</summary>
  
  O(n!)
</details>
<details>
  <summary>If a binary search tree is not balanced, how long might it take (worst case) to find an element in it?</summary>
  
  O(n), Where n is the number of nodes in the tree. the max time to find an element is the depth tree. The tree could be a straight list downwards and have depth n.
</details>
<details>
  <summary>You are looking for a specific value in a binary tree, but the tree is not a binary search tree. What is the time complexity of this?</summary>
  
  O(n). Without ant ordering property on the nodes, we might have to search through all the nodes.
</details>
<details>
  <summary>Calculate the following time complexities</summary>
  
  <details>
  <summary>Exercise 1</summary>
  
  ```java
int product(int a, int b) {
	int sum = 0;
	for (int i= 0; i < b; i++) {
		sum += a;
	}

	return sum;
}
```
   <details>
   <summary>Answer</summary>
    
***O(b)***. The for loop just iterates through b.
   </details>
  </details>
  <details>
  <summary>Exercise 2</summary>
  
  ```java
int power(int a, int b) {
	if (b < 0) {
		return 0; // error
	} else if (b == 0) {
		return 1;
	} else {
		return a * power(a, b - 1);
	}
}
```
   <details>
   <summary>Answer</summary>
    
***O(b)***. The recursive code iterates through b calls, since it subtracts one at each level.
   </details>
  </details>
  <details>
  <summary>Exercise 3</summary>
  
  ```java
int mod(int a, int b) {
	if (b <= 0) {
		return -1;
	}

	int div = a / b;
	return a - div * b;
}
```
   <details>
   <summary>Answer</summary>
    
***O(1)***. It does a constant amount of work.
   </details>
  </details>
  <details>
  <summary>Exercise 4</summary>
  
  ```java
int div(int a, int b) {
	int count = 0;
	int sum = b;
	while (sum <= a) {
		sum += b;
		count++;
	}

	return count;
}
```
   <details>
   <summary>Answer</summary>
    
***O(a/b)***.The variable count will eventually equal a/b. The while loop iterates count times. Therefore, it iterates a/b times.
   </details>
  </details>
  <details>
  <summary>Exercise 5</summary>
  
  ```java
int sqrt(int n) {
	return sqrt_helper(n, 1, n);
}

int sqrt_helper(int n, int min, int max) {
	if (max < min) return -1; // no square root
	
	int guess = (min + max) / 2;
	if (guess *guess == n) { // found it!
		return guess;
	} else if (guess * guess < n) { // too low
		return sqrt_helper(n, guess + 1, max); // try higher
	} else { // too high
		return sqrt_helper(n, min, guess - l); // try lower
	}
}
```
   <details>
   <summary>Answer</summary>
    
***O(log n)***. This algorithm is essentially doing a binary search to find the square root. Therefore, the runtime is ***O(log n)***.
   </details>
  </details>
  <details>
  <summary>Exercise 6</summary>
  
  ```java
int sqrt(int n) {
	for (int guess = 1; guess * guess <= n; guess++) {
		if (guess * guess == n) {
			return guess;
		}
	}

return -1;
}
```
   <details>
   <summary>Answer</summary>
    
***O(sqrt(n))***. This is just straightforward loop that stops when guess*guess > n (or, in other words, when guess > ***sqrt(n)***)
   </details>
  </details>
  <details>
  <summary>Exercise 7</summary>
  
  The ***appendToNew*** method appends a value to an array by creating a new, longer array and returning this longer array. You've used the ***appendToNew*** method to create a ***copyArray*** function that repeatedly calls ***appendToNew***. How long does copying an array take?

```java
int[] copyArray(int[] array) {
	int[] copy= new int[0];
	for (int value : array) {
		copy = appendToNew(copy, value);
	}
	
	return copy;
}

int[] appendToNew(int[] array, int value) {
	// copy all elements over to new array
	int[] bigger= new int[array.length + 1];
	for (int i= 0; i < array.length; i++) {
		bigger[i] = array[i];
	}

	// add new element
	bigger[bigger.length - 1] = value;
	return bigger;
	
}
```
   <details>
   <summary>Answer</summary>
    
***O(n^2)***. Where n is the number elements in the array. The first call to ***appendToNew*** takes 1 copy. The second call takes 2 copies. The third call takes 3 copies. And so on. The total time will be the sum of 1 through n, which is ***O(n^2)***.
   </details>
  </details>
  <details>
  <summary>Exercise 8</summary>
  
  ```java
int sumDigits(int n) {
	int sum = 0;
	while (n > 0) {
		sum += n % 10;
		n /= 10;
	}

	return sum;
}
```
   <details>
   <summary>Answer</summary>
    
***O(log n)***. The runtime will be the number of digits in the number. A number with d digits can have a value up to 10^d. if n = 10^d, the d = log n.
Therefore, the runtime is ***O(log n)***.
   </details>
  </details>
  <details>
  <summary>Exercise 9</summary>
  
  The following code prints all strings of length k where the characters are in sorted order. It does this by generating all strings of length k and then checking if each is sorted. What is its
runtime?

```java
int numChars = 26;

void printSortedStrings(int remaining) {
	printSortedStrings(remaining, "");
}

void printSortedStrings(int remaining, String prefix) {
	if (remaining == 0) {
		if (isinOrder(prefix)) {
			System.out.println(prefix);
		}
	} else {
			for (int i = 0; i < numchars; i++) {
				char c = ithletter(i);
				printSortedStrings(remaining - 1, prefix + c);
			}
	}
}

boolean isinOrder(String s) {
	for (int i= 1; i < s.length(); i++) {
		int prev = ithLetter(s.charAt(i - 1));
		int curr = ithLetter(s.charAt(i));
		
		if (prev > curr) {
			return false;
		}
	}

	return true;
}

char ithLetter(int i) {
	return (char) (((int) 'a') + i);
}
```
   <details>
   <summary>Answer</summary>
    
***O(k c^k)***. Where k is the length of the string and c is the number of characters in the alphabet. It takes ***O(c^k)*** time to generate each string. Then, we need to check that each of these is sorted, which takes ***O(k)*** time.
   </details>
  </details>
  <details>
  <summary>Exercise 10</summary>
  
  The following code computes the intersection (the number of elements in common) of two arrays. It assumes that neither array has duplicates. It computes the intersection by sorting
one array (array b) and then iterating through array a checking (via binary search) if each value is in b. What is its runtime?

```java
int intersection(int[] a, int[] b) {
	mergesort(b);
	int intersect = 0;
	
	for (int x : a) {
		if (binarySearch(b, x) >= 0) {
			intersect++;
		}
	}

	return intersect;
}
```
   <details>
   <summary>Answer</summary>
    
***O(b log b + a log b)***. First, we have to sort array b, which takes ***O(b log b)*** time. Then, for each element in a, we do binary search in ***O(log b)*** time. The second part takes ***O(a log b)*** time.
   </details>
  </details>
</details>


In computer science, the **time complexity** is the computational complexity that describes the amount of time it takes to run an algorithm.

Time complexity is commonly estimated by counting the number of elementary operations performed by the algorithm, supposing that each elementary operation takes a fixed amount of time to perform.

#### Example
Imagine a classroom of 100 students in which you gave your pen to one person. Now, you want that pen. Here are some ways to find the pen and what the O order is.

**O(n^2):** You go and ask the first person of the class, if he has the pen. Also, you ask this person about other 99 people in the classroom if they have that pen and so on,This is what we call O(n^2).

**O(n):** Going and asking each student individually is O(N).

**O(log n):** Now I divide the class into two groups, then ask: “Is it on the left side, or the right side of the classroom?” Then I take that group and divide it into two and ask again, and so on. Repeat the process till you are left with one student who has your pen. This is what you mean by O(log n).

I might need to do the O(n^2) search if only one student knows on which student the pen is hidden. I’d use the O(n) if one student had the pen and only they knew it. I’d use the O(log n) search if all the students knew, but would only tell me if I guessed the right side.

#### Order of Growth
**Order of Growth** is how the time of execution defends on the length of the input. Order of growth will help us to compute the running time with ease. We will ignore the lower order terms, since the lower order terms are relatively insignificant for large input. We use different notation to describe limiting behavior of a function.

#### O-notation

To denote asymptotic upper bound we use ***O-notation***. for a given function g(n), we denote O(g(n)) by:

![https://s3.us-west-2.amazonaws.com/secure.notion-static.com/f671876f-1de2-4a0f-a1cc-f3441544f3a0/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAT73L2G45O3KS52Y5%2F20200621%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20200621T034056Z&X-Amz-Expires=86400&X-Amz-Signature=81fc4c5aba45f578d98925877f9640fbc6cf2ea094891163a636e0f9bf99e6ef&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/f671876f-1de2-4a0f-a1cc-f3441544f3a0/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAT73L2G45O3KS52Y5%2F20200621%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20200621T034056Z&X-Amz-Expires=86400&X-Amz-Signature=81fc4c5aba45f578d98925877f9640fbc6cf2ea094891163a636e0f9bf99e6ef&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22)

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/777cb8b4-477c-40fb-8522-1569018de115/Untitled.png](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/777cb8b4-477c-40fb-8522-1569018de115/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAT73L2G45O3KS52Y5%2F20200621%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20200621T034203Z&X-Amz-Expires=86400&X-Amz-Signature=deddb1b51b7265a98bfb3529d6639cd22291cbe21184a3ca8042df3839bbdaee&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22)

While analyzing an algorithm, we mostly consider O-notation because it will give us an upper limit of the execution time, which is the worst case scenario.


#### Ω-notation

To denote asymptotic lower bound, we use ***Ω-notation***. for a given function g(n), we denote Ω(g(n)) by:

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/b55715ca-7a4c-4065-bfc4-cb181ecc0b0b/Untitled.png](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/b55715ca-7a4c-4065-bfc4-cb181ecc0b0b/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAT73L2G45O3KS52Y5%2F20200621%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20200621T034340Z&X-Amz-Expires=86400&X-Amz-Signature=36ddaba359f975ebff9b9df1e2bcd75a65ab0d78f64b52996fdded0adfbf5c81&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22)

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/57c555ad-e631-443c-8c50-309afe1dfb57/Untitled.png](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/57c555ad-e631-443c-8c50-309afe1dfb57/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAT73L2G45O3KS52Y5%2F20200621%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20200621T034345Z&X-Amz-Expires=86400&X-Amz-Signature=8bbb9e7eb038d8995e2149f3d8267ae29bd1143d2ac51a25a07ce447dca0d142&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22)

#### θ-notation

To denote asymptotic tight bound, we use ***θ-notation***. For a given function g(n), we denote θ(g(n)) by: 

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/187fa34f-23c1-4c5b-a7b7-3baf97fe05db/Untitled.png](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/187fa34f-23c1-4c5b-a7b7-3baf97fe05db/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAT73L2G45O3KS52Y5%2F20200621%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20200621T034421Z&X-Amz-Expires=86400&X-Amz-Signature=fde038fc0c3fcb1bf540dc5eb3743c3a5e3bd26e7d8b631a21aa4c6ed7320636&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22)

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/d3d1eaa1-ea82-43cc-ace1-b4acdeeb6572/Untitled.png](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/d3d1eaa1-ea82-43cc-ace1-b4acdeeb6572/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAT73L2G45O3KS52Y5%2F20200621%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20200621T034425Z&X-Amz-Expires=86400&X-Amz-Signature=2641f2539ca60b4ef274ad1501fb81a93e6d2d26798bebbbaecd14c261cd007f&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22)


## Common Complexities

- ***Constant Time - O(1)***

    O(1) describes algorithms that take the same amount of time to compute regardless of the input size.

    For instance, if a function takes the identical time to process ten elements as well as 1 million items, then we say that it has a constant growth rate or O(1).

    - ***Examples***
        - ***Odd or Even***

            Find if a number is odd or even.

            ```jsx
            function isEvenOrOdd(n) {
              return n % 2 ? 'Odd' : 'Even';
            }

            console.log(isEvenOrOdd(10)); // => Even
            console.log(isEvenOrOdd(10001)); // => Odd
            ```

            It doesn’t matter if ***n*** is 10 or 10,001, it will execute line 2 one time.

        - ***Look-up Table***

            Given a string, find its word frequency data.

            ```jsx
            const dictionary = {the: 22038615, be: 12545825, and: 10741073, of: 10343885, a: 10144200, in: 6996437, to: 6332195 /* ... */};

            function getWordFrequency(dictionary, word) {
              return dictionary[word];
            }

            console.log(getWordFrequency(dictionary, 'the'));
            console.log(getWordFrequency(dictionary, 'in'));
            ```

            Again, we can be sure that even if the dictionary has 10 or 1 million words, it would still execute line 4 once to find the word. However, if we decided to store the dictionary as an array rather than a hash map, then it would be a different story.

- ***Linear Time - O(n)***

    These algorithms imply that the program visits every element from the input.

    Linear time complexity O(n) means that as the input grows, the algorithms  take proportionally longer to complete.

    - ***Examples***
        - ***The Largest Item On an Unsorted Array***

            Let's say you want to find the maximum value from an unsorted array.

            ```jsx
            function findMax(n) {
              let max;
              let counter = 0;

              for (let i = 0; i < n.length; i++) {
                counter++;
                if(max === undefined || max < n[i]) {
                  max = n[i];
                }
              }

              console.log(`n: ${n.length}, counter: ${counter}`);
              return max;
            }
            ```

            How many operations will the ***findMax*** function do?

            Well, it checks every element from ***n***. if the current item is more significant than max, it will do an assignment.

            Notice that we added a counter so it can help us count h many times the inner block executed.

            If you get the time complexity, it would be something like this:

            - ***Line 2-3:*** 2 operations
            - ***Line 4:*** a loop of size n
            - ***Line 6-8:*** 3 operations inside the for-loop.

            So, this gets us 3(n) + 2. we only need the biggest order term, thus O(n).

            If we plot it n and ***findMax*** running time, we will have a graph like a linear equation.

            ![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/6568f520-f372-45d9-97ac-6551e60d2df3/Untitled.png](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/6568f520-f372-45d9-97ac-6551e60d2df3/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAT73L2G45O3KS52Y5%2F20200621%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20200621T034704Z&X-Amz-Expires=86400&X-Amz-Signature=7f00b39c98d88ca0c4982427f86d13b8a50301be87976782f4e33ee7ab632935&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22)

- ***Quadratic Time - O(n^2)***

    A function with a quadratic time complexity has a growth rate of  `n^2`. if the input is size 2, it will do 4 operations. if the input is size 8. it will take 64, and so on.

    - ***Examples***
        - ***Has Duplicates***

            You want to find duplicate words in an array. A naive solution will be the following:

            ```jsx
            function hasDuplicates(n) {
              const duplicates = [];
              let counter = 0;

              for (let outter = 0; outter < n.length; outter++) {
                for (let inner = 0; inner < n.length; inner++) {
                  counter++;

                  if(outter === inner) continue;

                  if(n[outter] === n[inner]) {
                    return true;
                  }
                }
              }

              console.log(`n: ${n.length}, counter: ${counter}`);
              return false;
            }
            ```

            Time complexity analysis:

            - Line 2-3: 2 operations
            - Line 5-6: double-loop of size n, so `n^2`.
            - Line 7-13: has ~3 operations inside the double-loop

            We get `3n^2 + 2`.

            Again, when we have an asymptotic analysis, we drop all constants and leave the most important term: `n^2`. So, in big O notation, it would be O(n^2).

            We are using a counter variable to help us verify. The hasDuplicates function has two loops. If we have an input of 4 words, it will execute the inner block 16 times. If we have 9, it will perform counter 81 times and so forth.

            ```jsx
            hasDuplicates([1,2,3,4]);
            // n: 4, counter: 16
            ```

            and with n size 9:

            ```jsx
            hasDuplicates([1,2,3,4,5,6,7,8,9]);
            // n: 9, counter: 81
            ```

        - ***Bubble Sort***

            We want to sort the elements in an array.

            ```jsx
            function sort(n) {
              for (let outer = 0; outer < n.length; outer++) {
                let outerElement = n[outer];

                for (let inner = outer + 1; inner < n.length; inner++) {
                  let innerElement = n[inner];

                  if(outerElement > innerElement) {
                    // swap
                    n[outer] = innerElement;
                    n[inner] = outerElement;
                    // update references
                    outerElement = n[outer];
                    innerElement = n[inner];
                  }
                }
              }
              return n;
            }
            ```

            Also, you might notice that for a colossal n, the time it takes to solve the problem increases a lot. Can you spot the relationship between nested loops and the running time? When a function has a single loop, it usually translates into a running time complexity of O(n). Now, this function has 2 nested loops and quadratic running time: O(n^2).

- ***Polynomial Time - O(n^c)***

    Polynomial running is represented as O(n^c), when `c > 1`. As you already saw, two inner loops almost translate to O(n^2) since it has to go through the array twice in most cases. Are three nested loops cubic? If each one visit all elements, then yes!

    Usually, we want to stay away from polynomial running times (quadratic, cubic, n^c, etc.) since they take longer to compute as the input grows fast. However, they are not the worst.

    - ***Examples***
        - ***Three nested loops***

            Let’s say you want to find the solutions for a multi-variable equation that looks like this:

            > 3x + 9y + 8z = 79

            This naive program will give you all the solutions that satisfy the equation where x, y, and z < n.

            ```jsx
            function findXYZ(n) {
              const solutions = [];

              for(let x = 0; x < n; x++) {
                for(let y = 0; y < n; y++) {
                  for(let z = 0; z < n; z++) {
                    if( 3*x + 9*y + 8*z === 79 ) {
                      solutions.push({x, y, z});
                    }
                  }
                }
              }

              return solutions;
            }

            console.log(findXYZ(10)); // => [{x: 0, y: 7, z: 2}, ...]
            ```

            This algorithm has a cubic running time: `O(n^3)`.

            **Note:** We could do a more efficient solution to solve multi-variable equations but this works for the purpose of showing an example of a cubic runtime.

- ***Logarithmic Time - O(log n)***

    Logarithmic time complexities usually apply to algorithms that divide problems in half every time. For instance, let’s say that we want to look for a book in a dictionary. As you know, this book has every word sorted alphabetically. If you are looking for a word, then there are at least two ways to do it:

    ***Algorithm A:***

    1. Start on the first page of the book and go word by word until you find what you are looking for.

    ***Algorithm B:***

    1. Open the book in the middle and check the first word on it.
    2. If the word that you are looking for is alphabetically more significant, then look to the right. Otherwise, look in the left half.
    3. Divide the remainder in half again, and repeat step #2 until you find the word you are looking for.

    Which one is faster? The first algorithms go word by word *O(n)*, while the algorithm B split the problem in half on each iteration *O(log n)*. This 2nd algorithm is a **binary search**.

    - ***Examples***
        - ***Binary Search***

            Find the index of an element in a sorted array.

            If we implement (Algorithm A) going through all the elements in an array, it will take a running time of `O(n)`. Can we do better? We can try using the fact that the collection is already sorted. Later, we can divide in half as we look for the element in question.

            ```jsx
            function indexOf(array, element, offset = 0) {
              // split array in half
              const half = parseInt(array.length / 2);
              const current = array[half];

              if(current === element) {
                return offset + half;
              } else if(element > current) {
                const right = array.slice(half);
                return indexOf(right, element, offset + half);
              } else {
                const left = array.slice(0, half)
                return indexOf(left, element, offset);
              }
            }

            // Usage example with a list of names in ascending order:
            const directory = ["Adrian", "Bella", "Charlotte", "Daniel", "Emma", "Hanna", "Isabella", "Jayden", "Kaylee", "Luke", "Mia", "Nora", "Olivia", "Paisley", "Riley", "Thomas", "Wyatt", "Xander", "Zoe"];
            console.log(indexOf(directory, 'Hanna'));   // => 5
            console.log(indexOf(directory, 'Adrian'));  // => 0
            console.log(indexOf(directory, 'Zoe'));     // => 18
            ```

            Calculating the time complexity of `indexOf` is not as straightforward as the previous examples. This function is recursive.

            There are several ways to analyze recursive algorithms. For simplicity, we are going to use the `Master Method`.

- ***Linearithmic Time - O(n log n)***

    Linearithmic time complexity it’s slightly slower than a linear algorithm. However, it’s still much better than a quadratic algorithm

    - ***Examples***
        - ***Merge sort***

            What’s the best way to sort an array? Before, we proposed a solution using bubble sort that has a time complexity of O(n2). Can we do better?

            We can use an algorithm called `merge sort` to improve it. This is how merge sort works:

            1. We are going to divide the array recursively until the elements are two or less.
            2. We know how to sort two items, so we sort them iteratively (base case).
            3. The final step is merging: we merge in taking one by one from each array such that they are in ascending order.

            Here’s the code for merge sort:

            ```jsx
            /**
             * Sort array in asc order using merge-sort
             * @example
             *    sort([3, 2, 1]) => [1, 2, 3]
             *    sort([3]) => [3]
             *    sort([3, 2]) => [2, 3]
             * @param {array} array
             */
            function sort(array = []) {
              const size = array.length;
              // base case
              if (size < 2) {
                return array;
              }
              if (size === 2) {
                return array[0] > array[1] ? [array[1], array[0]] : array;
              }
              // slit and merge
              const mid = parseInt(size / 2, 10);
              return merge(sort(array.slice(0, mid)), sort(array.slice(mid)));
            }

            /**
             * Merge two arrays in asc order
             * @example
             *    merge([2,5,9], [1,6,7]) => [1, 2, 5, 6, 7, 9]
             * @param {array} array1
             * @param {array} array2
             * @returns {array} merged arrays in asc order
             */
            function merge(array1 = [], array2 = []) {
              const merged = [];
              let array1Index = 0;
              let array2Index = 0;
              // merge elements on a and b in asc order. Run-time O(a + b)
              while (array1Index < array1.length || array2Index < array2.length) {
                if (array1Index >= array1.length || array1[array1Index] > array2[array2Index]) {
                  merged.push(array2[array2Index]);
                  array2Index += 1;
                } else {
                  merged.push(array1[array1Index]);
                  array1Index += 1;
                }
              }
              return merged;
            }
            ```

            As you can see, it has two functions sort and merge. Merge is an auxiliary function that runs once through the collection a and b, so it’s running time is O(n). Let’s apply the Master Method to find the running time.

            1) Let’s find the values of: `T(n) = a T(n/b) + f(n)`

            - `a`: The number of sub-problems is 2 (line 12). So, `a = 2`.
            - `b`: Each of the sub-problems divides `n` in half. So, `b = 2`
            - `f(n)`: The work done outside the recursion is the function `merge`, which has a runtime of `O(n)` since it visits all the elements on the given arrays.

            Substituting the values:

            > T(n) = 2 T(n/2) + O(n)

            2) Let’s find the work done in the recursion: `n^logb(a)`.

            n^log2(2)

            n^1 = n

            3) Finally, we can see that recursion runtime from step 2) is O(n) and also the non-recursion runtime is O(n). So, we have the [case 2](https://adrianmejia.com/most-popular-algorithms-time-complexity-every-programmer-should-know-free-online-tutorial-course/#Case-2-The-runtime-of-the-work-done-in-the-recursion-and-outside-is-the-same) : `O(n^logb(a) * log(n))`

            O(n^log2(2) log(n))

            O(n1 log(n))

            O(n log(n)) **👈 this is running time of the merge sort**

- ***Exponential Time - O(2^n)***

    Exponential (base 2) running time means that the calculations performed by an algorithm double every time as the input grows.

    - ***Examples***
        - ***Power Set***

            To understand the power set, let’s imagine you are buying a pizza. The store has many toppings that you can choose from like pepperoni, mushrooms, bacon, and pineapple. Let’s call each topping A, B, C, D. What are your choices? You can select no topping (you are on a diet ;), you can choose one topping, or two or three or all of them, and so on. The power set gives you all the possibilities (BTW, there 16 with 4 toppings as you will see later)

            Finding all distinct subsets of a given set. For instance, let’s do some examples to try to come up with an algorithm to solve it:

            ```jsx
            powerset('') // =>  ['']
            powerset('a') // => ['', 'a']
            powerset('ab') // => ['', 'a', 'b', 'ab']
            ```

            Did you notice any pattern?

            - The first returns an empty element.
            - The second case returns the empty element + the 1st element.
            - The 3rd case returns precisely the results of 2nd case + the same array with the 2nd element `b` appended to it.

            What if you want to find the subsets of `abc`? Well, it would be precisely the subsets of ‘ab’ and again the subsets of `ab` with `c` appended at the end of each element.

            As you noticed, every time the input gets longer, the output is twice as long as the previous one. Let’s code it:

            ```jsx
            function powerset(n = '') {
              const array = Array.from(n);
              const base = [''];

              const results = array.reduce((previous, element) => {
                const previousPlusElement = previous.map(el => {
                  return `${el}${element}`;
                });
                return previous.concat(previousPlusElement);
              }, base);

              return results;
            }
            ```

            If we run that function for a couple of cases we will get:

            ```jsx
            powerset('') // ...
            // n = 0, f(n) = 1;
            powerset('a') // , a...
            // n = 1, f(n) = 2;
            powerset('ab') // , a, b, ab...
            // n = 2, f(n) = 4;
            powerset('abc') // , a, b, ab, c, ac, bc, abc...
            // n = 3, f(n) = 8;
            powerset('abcd') // , a, b, ab, c, ac, bc, abc, d, ad, bd, abd, cd, acd, bcd...
            // n = 4, f(n) = 16;
            powerset('abcde') // , a, b, ab, c, ac, bc, abc, d, ad, bd, abd, cd, acd, bcd...
            // n = 5, f(n) = 32;
            ```

            As expected, if you plot `n` and `f(n)`, you will notice that it would be exactly like the function `2^n`. This algorithm has a running time of `O(2^n)`.

            **Note:** You should avoid functions with exponential running times (if possible) since they don’t scale well. The time it takes to process the output doubles with every additional input size. But exponential running time is not the worst yet; others go even slower.

- ***Factorial Time - O(n!)***

    Factorial is the multiplication of all positive integer numbers less than itself. For instance:

    > 5! = 5 x 4 x 3 x 2 x 1 = 120

    It grows pretty quickly:

    > 20! = 2,432,902,008,176,640,000

    As you might guess, you want to stay away if possible from algorithms that have this running time!

    - ***Examples***
        - ***Permutations***

            Write a function that computes all the different words that can be formed given a string. E.g.

            ```jsx
            getPermutations('a') // => [ 'a']
            getPermutations('ab') // =>  [ 'ab', 'ba']
            getPermutations('abc') // => [ 'abc', 'acb', 'bac', 'bca', 'cab', 'cba' ]
            ```

            How would you solve that?

            A straightforward way will be to check if the string has a length of 1 if so, return that string since you can’t arrange it differently.

            For strings with a length bigger than 1, we could use recursion to divide the problem into smaller problems until we get to the length 1 case. We can take out the first character and solve the problem for the remainder of the string until we have a length of 1.

            ```jsx
            function getPermutations(string, prefix = '') {
              if(string.length <= 1) {
                return [prefix + string];
              }

              return Array.from(string).reduce((result, char, index) => {
                const reminder = string.slice(0, index) + string.slice(index+1);
                result = result.concat(getPermutations(reminder, prefix + char));
                return result;
              }, []);
            }
            ```

            If print out the output, it would be something like this:

            ```jsx
            getPermutations('ab') // ab, ba...
            // n = 2, f(n) = 2;
            getPermutations('abc') // abc, acb, bac, bca, cab, cba...
            // n = 3, f(n) = 6;
            getPermutations('abcd') // abcd, abdc, acbd, acdb, adbc, adcb, bacd...
            // n = 4, f(n) = 24;
            getPermutations('abcde') // abcde, abced, abdce, abdec, abecd, abedc, acbde...
            // n = 5, f(n) = 120;
            ```


## Running Complexities Graphs
![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/821a126d-3e8c-4cd1-83d0-85aef0e3705e/Untitled.png](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/821a126d-3e8c-4cd1-83d0-85aef0e3705e/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAT73L2G45O3KS52Y5%2F20200621%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20200621T034827Z&X-Amz-Expires=86400&X-Amz-Signature=e88d12b9c732c7171cff3fd998447f10ebdb200b21c4cff46d16b15b097856f9&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22)


## Recursive Algorithms

### Master Method

first, lets look at a binary search algorithm, and try to analyze it's time complexity.

```jsx
function indexOf(array, element, offset = 0) {
  // split array in half
  const half = parseInt(array.length / 2);
  const current = array[half];

  if(current === element) {
    return offset + half;
  } else if(element > current) {
    const right = array.slice(half);
    return indexOf(right, element, offset + half);
  } else {
    const left = array.slice(0, half)
    return indexOf(left, element, offset);
  }
}

// Usage example with a list of names in ascending order:
const directory = ["Adrian", "Bella", "Charlotte", "Daniel", "Emma", "Hanna", "Isabella", "Jayden", "Kaylee", "Luke", "Mia", "Nora", "Olivia", "Paisley", "Riley", "Thomas", "Wyatt", "Xander", "Zoe"];
console.log(indexOf(directory, 'Hanna'));   // => 5
console.log(indexOf(directory, 'Adrian'));  // => 0
console.log(indexOf(directory, 'Zoe'));     // => 18
```

Finding the runtime of recursive algorithms is not as easy as counting the operations. This method helps us to determine the runtime of recursive algorithms. We are going to explain this solution using the indexOf function as an illustration.

When analyzing recursive algorithms, we care about these three things:

- The runtime of the work done outside the recursion (line 3-4): `O(1)`
- How many recursive calls the problem is divided (line 11 or 14): `1` recursive call. Notice only one or the other will happen, never both.
- How much `n` is reduced on each recursive call (line 10 or 13): `1/2`. Every recursive call cuts `n` in half.

1) The Master Method formula is the following:

> T(n) = a T(n/b) + f(n)

where:

- `T`: time complexity function in terms of the input size `n`.
- `n`: the size of the input. duh? :)
- `a`: the number of sub-problems. For our case, we only split the problem into one subproblem. So, `a=1`.
- `b`: the factor by which `n` is reduced. For our example, we divide `n` in half each time. Thus, `b=2`.
- `f(n)`: the running time outside the recursion. Since dividing by 2 is constant time, we have `f(n) = O(1)`.

2) Once we know the values of a, b and f(n). We can determine the runtime of the recursion using this formula:

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/d12364d3-6328-4e0b-a079-358b8ea1120b/Untitled.png](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/d12364d3-6328-4e0b-a079-358b8ea1120b/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAT73L2G45O3KS52Y5%2F20200621%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20200621T035043Z&X-Amz-Expires=86400&X-Amz-Signature=a6619b21443503a47979ba20590c478637de97565b6ce956b3ee118172c36058&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22)

This value will help us to find which master method case we are solving.

For binary search, we have:

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/48684e7d-f9a2-4de2-9fe9-0319596a292d/Untitled.png](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/48684e7d-f9a2-4de2-9fe9-0319596a292d/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAT73L2G45O3KS52Y5%2F20200621%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20200621T035104Z&X-Amz-Expires=86400&X-Amz-Signature=f3f7501530e690bcf5acf400395918d5911671dec3b70ed208b58199a8ced5c0&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22)

3) Finally, we compare the recursion runtime from step 2) and the runtime `f(n)` from step 1). Based on that, we have the following cases:

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/9990695c-88a6-4b33-883b-d95489c60b82/Untitled.png](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/9990695c-88a6-4b33-883b-d95489c60b82/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAT73L2G45O3KS52Y5%2F20200621%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20200621T035125Z&X-Amz-Expires=86400&X-Amz-Signature=634ce58a8e87388175617afaa23420faf11abf095f08e8ccc504ca2f9493c729&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22)

Now, let’s combine everything we learned here to get the running time of our binary search function indexOf.

The binary search algorithm slit n on half until a solution is found or array is exhausted. So, using the Master Method:

> T(n) = a T(n/b) + f(n)

1) Find `a`, `b` and `f(n)` and replace it in the formula:

- `a`: the number of sub-problems. For our example, we only split the problem into another subproblem. So `a=1`.
- `b`: the factor by which `n` is reduced. For our case, we divide `n` in half each time. Thus, `b=2`.
- `f(n)`: the running time outside the recursion: `O(1)`.

Thus,

> T(n) = T(n/2) + O(1)

2) Compare the runtime executed inside and outside the recursion:

- Runtime of the work done **outside** the recursion: `f(n)`. E.g. `O(1)`.
- Runtime of work done **inside** the recursion given by this formula `nlogba`. E.g. O(`nlog21`) = O(`n0`) = `O(1)`.

3) Finally, getting the runtime. Based on the comparison of the expressions from the previous steps, find the case it matches.

As we saw in the previous step, the work outside and inside the recursion has the same runtime, so we are in **case 2**.

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/1845b30a-57b4-420c-8204-844f4adef823/Untitled.png]https://s3.us-west-2.amazonaws.com/secure.notion-static.com/1845b30a-57b4-420c-8204-844f4adef823/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAT73L2G45O3KS52Y5%2F20200621%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20200621T035147Z&X-Amz-Expires=86400&X-Amz-Signature=6b7e27c38e592e46eb342ed53ea1aa27053bda8f035f9e0584cb83a216681d3e&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22)

Making the substitution we get:

O(n^log2(1) log(n))

O(n^0 log(n))

O(log(n)) **👈 this is running time of a binary search**

