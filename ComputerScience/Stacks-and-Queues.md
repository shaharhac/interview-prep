## Stack

Stack is a linear data structure which follows a paricular order in which the opearions are performed. The order is LIFO (Last In Fist Out).
A good example of a stack are plates stacked over one another. The plate which is at the top is the first one to be removed.

<details>
<summary> Implemantation using Javascript </summary>

both `array.push()` and `array.pop` are `O(1)`

```jsx
class Stack {
    constructor(){
        this.data = [];
        this.top = 0;
    }

    push(element) {
      this.data.push(element);
      this.top = this.top + 1;
    }

    peek() {
      return this.data[this.top - 1]
    }

    pop() {
      if(this.isEmpty()) throw "underflow";
     
      this.top = this.top - 1;
      return this.data.pop();
    }

    isEmpty() {
      return this.top === 0;
    }
}
```

</details>

## Queue

A Queue is a linear structur which follow a particular order in which the operations are performed. The order is First in First OUt (FIFO).
a Goode example of a queue is any queue of consumers for a resource where the consumer that came first is served first.

<details>
<summary> Implemantation using Javascript </summary>

```jsx
class Queue {
  constructor() { 
    this.items = []; 
  } 

  enqueue(element) {
    this.items.push(element)
  }

  dequeue() {
    if(this.isEmpty()) throw "underflow";

    return this.items.shift();
  }

  front() {
    if(this.isEmpty()) return "no elements"

    return this.items[0]
  }

  isEmpty() {
    return this.items.length === 0;
  }
}
```

</details>
