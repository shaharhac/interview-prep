
try to answer the questions below first, then read the rest of the page

<details>
<summary>What is the event loop?</summary>

The event loop is responsible for executing the code, collecting and processing events, and executing queued sub-tasks.
</details>

<details>
<summary>Draw the JS program flow architecture</summary>

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/8a478845-8ae6-40f6-abb5-dc7db944991c/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/8a478845-8ae6-40f6-abb5-dc7db944991c/Untitled.png)
</details>

<details>
<summary>Explain the use of each of the component in the archutecture above</summary>

### Heap

Objects are allocated in a heap which is just a name to denote a large mostly unstructured region of memory

### Call Stack

The Call Stack is a data structure which records basically where in the program we are. If we step into a function, we put it on the top of the stack. If we return from a function, we pop off the top of the stack. That’s all the stack can do.

### Callback Queue

JavaScript runtimes contain a message queue that stores a list of messages to be processed and their associated callback functions.

### Browser or Web APIs

In essence, they are threads that you can’t access, you can just make calls to them. They are the pieces of the browser in which concurrency kicks in. If you’re a Node.js developer, these are the C++ APIs.
</details>

<details>
<summary>Explain what is "stack overflow"</summary>

this happens when you reach the maximum Call Stack size. And that could happen quite easily, especially if you’re using recursion without testing your code very extensively. Take a look at this sample code:

```jsx
function foo() {
    foo();
}
foo();
```

When the engine starts executing this code, it starts with calling the function “foo”. This function, however, is recursive and starts calling itself without any termination conditions. So at every step of the execution, the same function gets added to the Call Stack over and over again. It looks something like this:

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/1396a3bb-0757-4f1d-ad71-97fd427c3f68/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/1396a3bb-0757-4f1d-ad71-97fd427c3f68/Untitled.png)
</details>

<details>
<summary>Explain what Blocking Code is and how to prevent it</summary>

When a message (a function for example) takes too long to complete, the web application is unable to process user interactions like click or scroll - because those interactions happens on the same thread as the code itself. The browser mitigates this with the "a script is taking too long to run" dialog.

we can run heavy code without blocking the UI and making the browser unresponsive with smart use of **asynchronous callbacks** (for example, divide the blocking message into several messages).
</details>

<details>
<summary>What is the v8?</summary>

The V8 is the most popular JavaScript engine, and being used in Google Chrome and NodeJS.

It was built by google, written in C++ and is open source.

A JavaScript engine is a program or an interpreter which executes JavaScript code.
</details>

<details>
<summary>What is the difference between Asynchronous and Non-blocking?</summary>

Asynchronous literally means not synchronous. We are making HTTP requests which are asynchronous, means we are not waiting for the server response. We continue with other block and respond to the server response when we received.

The term Non-Blocking is widely used with IO. For example non-blocking read/write calls return with whatever they can do and expect caller to execute the call again. Read will wait until it has some data and put calling thread to sleep.
</details>

<details>
<summary>Whats the difference between requestAnimationFrame() and setTimeout()</summary>

`setTimeout` attaches a handler to the base event loop, always attaching to the next iteration of the event loop, which is almost 10ms from current time, but the exact delay depends on browser implementation.

`requestAnimationFrame` attaches handler to the next “render” loop iteration, instead of event loop. If you want to update UI in every iteration, then this is the most efficient place to update DOM because browser renders the DOM right after.
</details>

<details>
<summary>Difference between setImmediate() vs setTimeout()</summary>

`setImmediate()` and `setTimeout()` are similar but behave in different ways depending on when they are called.

- `setImmediate()` is designed to execute a script once the current poll (event loop) phase completes.
- `setTimeout()` schedules a script to be run after a minimum threshold in ms has elapsed.

The order in which the timers are executed will vary depending on the context in which they are called. If both are called from within the main module, then timing will be bound by the performance of the process.
</details>

<details>
<summary>What is process.nextTick()?</summary>

This function schedules a callback function which is required to be invoked in the next iteration of the event loop
</details>



the **Event Loop** is used by JavaScript to execute code, collect and process events, and executing queued sub-tasks.

In JavaScript, almost all I/O is non-blocking. This includes HTTP requests, database operations, and disk reads and writes; the single thread of execution asks the runtime to perform an operation, providing a callback function and then moves on to do something else. When the operation has been completed, a message is enqueued along with the provided callback function. At some point in the future, the message is dequeued and the callback fired.

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/8a478845-8ae6-40f6-abb5-dc7db944991c/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/8a478845-8ae6-40f6-abb5-dc7db944991c/Untitled.png)

## Runtime Concepts

### Heap

Objects are allocated in a heap which is just a name to denote a large mostly unstructured region of memory

### Call Stack

The Call Stack is a data structure which records basically where in the program we are. If we step into a function, we put it on the top of the stack. If we return from a function, we pop off the top of the stack. That’s all the stack can do.

<details>
<summary>“Blowing the stack"</summary>

— this happens when you reach the maximum Call Stack size. And that could happen quite easily, especially if you’re using recursion without testing your code very extensively. Take a look at this sample code:

```jsx
function foo() {
    foo();
}
foo();
```

When the engine starts executing this code, it starts with calling the function “foo”. This function, however, is recursive and starts calling itself without any termination conditions. So at every step of the execution, the same function gets added to the Call Stack over and over again. It looks something like this:

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/1396a3bb-0757-4f1d-ad71-97fd427c3f68/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/1396a3bb-0757-4f1d-ad71-97fd427c3f68/Untitled.png)
</details>

### Callback Queue

JavaScript runtimes contain a message queue that stores a list of messages to be processed and their associated callback functions.

### Browser or Web APIs

In essence, they are threads that you can’t access, you can just make calls to them. They are the pieces of the browser in which concurrency kicks in. If you’re a Node.js developer, these are the C++ APIs.

The Event Loop has one simple job — to monitor the Call Stack and the Callback Queue. If the Call Stack is empty, it will take the first event from the queue and will push it to the Call Stack, which effectively runs it.

Such an iteration is called a **tick** in the Event Loop. Each event is just a function callback.

<details>
<summary>Open to see an example of the event loop</summary>

```jsx
console.log('Hi');
setTimeout(function cb1() { 
    console.log('cb1');
}, 5000);
console.log('Bye');
```

let's execute this code and see what happens

1. The state is clear. The browser console is clear, and the Call Stack is empty.

![https://miro.medium.com/max/1024/1*9fbOuFXJHwhqa6ToCc_v2A.png](https://miro.medium.com/max/1024/1*9fbOuFXJHwhqa6ToCc_v2A.png)

2. `console.log('Hi')` is added to the Call Stack.

![https://miro.medium.com/max/1024/1*dvrghQCVQIZOfNC27Jrtlw.png](https://miro.medium.com/max/1024/1*dvrghQCVQIZOfNC27Jrtlw.png)

3. `console.log('Hi')` is executed.

![https://miro.medium.com/max/1024/1*yn9Y4PXNP8XTz6mtCAzDZQ.png](https://miro.medium.com/max/1024/1*yn9Y4PXNP8XTz6mtCAzDZQ.png)

4. `console.log('Hi')` is removed from the Call Stack.

![https://miro.medium.com/max/1024/1*iBedryNbqtixYTKviPC1tA.png](https://miro.medium.com/max/1024/1*iBedryNbqtixYTKviPC1tA.png)

5. `setTimeout(function cb1() { ... })` is added to the Call Stack.

![https://miro.medium.com/max/1126/1*HIn-BxIP38X6mF_65snMKg.png](https://miro.medium.com/max/1126/1*HIn-BxIP38X6mF_65snMKg.png)

6. `setTimeout(function cb1() { ... })` is executed. The browser creates a timer as part of the Web APIs. It is going to handle the countdown for you.

![https://miro.medium.com/max/1024/1*vd3X2O_qRfqaEpW4AfZM4w.png](https://miro.medium.com/max/1024/1*vd3X2O_qRfqaEpW4AfZM4w.png)

7. The `setTimeout(function cb1() { ... })` itself is complete and is removed from the Call Stack.

![https://miro.medium.com/max/1024/1*_nYLhoZPKD_HPhpJtQeErA.png](https://miro.medium.com/max/1024/1*_nYLhoZPKD_HPhpJtQeErA.png)

8. `console.log('Bye')` is added to the Call Stack.

![https://miro.medium.com/max/1024/1*1NAeDnEv6DWFewX_C-L8mg.png](https://miro.medium.com/max/1024/1*1NAeDnEv6DWFewX_C-L8mg.png)

9. `console.log('Bye')` is executed.

![https://miro.medium.com/max/1024/1*UwtM7DmK1BmlBOUUYEopGQ.png](https://miro.medium.com/max/1024/1*UwtM7DmK1BmlBOUUYEopGQ.png)

10. `console.log('Bye')` is removed from the Call Stack.

![https://miro.medium.com/max/1024/1*-vHNuJsJVXvqq5dLHPt7cQ.png](https://miro.medium.com/max/1024/1*-vHNuJsJVXvqq5dLHPt7cQ.png)

11. After at least 5000 ms, the timer completes and it pushes the `cb1` callback to the Callback Queue.

![https://miro.medium.com/max/1024/1*eOj6NVwGI2N78onh6CuCbA.png](https://miro.medium.com/max/1024/1*eOj6NVwGI2N78onh6CuCbA.png)

12. The Event Loop takes `cb1` from the Callback Queue and pushes it to the Call Stack.

![https://miro.medium.com/max/1024/1*jQMQ9BEKPycs2wFC233aNg.png](https://miro.medium.com/max/1024/1*jQMQ9BEKPycs2wFC233aNg.png)

13. `cb1` is executed and adds `console.log('cb1')` to the Call Stack.

![https://miro.medium.com/max/1024/1*hpyVeL1zsaeHaqS7mU4Qfw.png](https://miro.medium.com/max/1024/1*hpyVeL1zsaeHaqS7mU4Qfw.png)

14. `console.log('cb1')` is executed.

![https://miro.medium.com/max/1024/1*lvOtCg75ObmUTOxIS6anEQ.png](https://miro.medium.com/max/1024/1*lvOtCg75ObmUTOxIS6anEQ.png)

15. `console.log('cb1')` is removed from the Call Stack.

![https://miro.medium.com/max/1024/1*Jyyot22aRkKMF3LN1bgE-w.png](https://miro.medium.com/max/1024/1*Jyyot22aRkKMF3LN1bgE-w.png)

16. `cb1` is removed from the Call Stack.

![https://miro.medium.com/max/1024/1*t2Btfb_tBbBxTvyVgKX0Qg.png](https://miro.medium.com/max/1024/1*t2Btfb_tBbBxTvyVgKX0Qg.png)
</details>

## Concurrency & the Event Loop

What happens when you have function calls in the Call Stack that take a huge amount of time in order to be processed? For example, imagine that you want to do some complex image transformation with JavaScript in the browser.

You may ask — why is this even a problem? The problem is that while the Call Stack has functions to execute, the browser can’t actually do anything else — it’s getting blocked. This means that the browser can’t render, it can’t run any other code, it’s just stuck. And this creates problems if you want nice fluid UIs in your app.

So, how can we execute heavy code without blocking the UI and making the browser unresponsive? Well, the solution is **asynchronous callbacks.**

### Run to completion

Each message is processed completely before any other message is processed.

This offers some nice properties when reasoning about your program, including the fact that whenever a function runs, it cannot be pre-empted and will run entirely before any other code runs (and can modify data the function manipulates). This differs from C, for instance, where if a function runs in a thread, it may be stopped at any point by the runtime system to run some other code in another thread.

A downside of this model is that if a message takes too long to complete, the web application is unable to process user interactions like click or scroll. The browser mitigates this with the "a script is taking too long to run" dialog. A good practice to follow is to make message processing short and if possible cut down one message into several messages.

### Adding Messages

In web browsers, messages are added anytime an event occurs and there is an event listener attached to it. If there is no listener, the event is lost. So a click on an element with a click event handler will add a message—likewise with any other event.

The function `[setTimeout](https://developer.mozilla.org/en-US/docs/Web/API/WindowTimers.setTimeout)` is called with 2 arguments: a message to add to the queue, and a time value (optional; defaults to `0`). The *time value* represents the (minimum) delay after which the message will actually be pushed into the queue. If there is no other message in the queue, and the stack is empty, the message is processed right after the delay. However, if there are messages, the `setTimeout` message will have to wait for other messages to be processed. For this reason, the second argument indicates a *minimum* time—not a *guaranteed* time. Here is an example that demonstrates this concept (`setTimeout` does not run immediately after its timer expires):

```jsx
const s = new Date().getSeconds();

setTimeout(function() {
  // prints out "2", meaning that the callback is not called immediately after 500 milliseconds.
  console.log("Ran after " + (new Date().getSeconds() - s) + " seconds");
}, 500)

while (true) {
  if (new Date().getSeconds() - s >= 2) {
    console.log("Good, looped for 2 seconds")
    break;
  }
}
```
