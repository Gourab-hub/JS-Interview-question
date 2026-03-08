# JS-Interview-question

1. What is a Closure in JavaScript?

A closure is a function that remembers and can access variables from its outer (parent) function scope, even after the outer function has finished executing.
```javascript
function outerFunction() {
  let count = 0;

  function innerFunction() {
    count++;
    console.log("Count:", count);
  }

  return innerFunction;
}

const counter = outerFunction();

counter(); // Count: 1
counter(); // Count: 2
counter(); // Count: 3
```

2. Why are closures useful?

Closures are useful for:

Data encapsulation / private variables
Function factories
Maintaining state
Callbacks and event handlers
Currying

3. What is a Promise in JavaScript?

A Promise is an object that represents the result of an asynchronous operation that may complete in the future.

A Promise has 3 states:

Pending – operation is still running
Fulfilled (Resolved) – operation completed successfully
Rejected – operation failed
```javascript
fetch("https://jsonplaceholder.typicode.com/users")
  .then(response => response.json())
  .then(data => console.log(data))
  .catch(error => console.log(error));
```

We use promises when working with asynchronous operations, such as:

API calls
Database requests
File reading
Timers (setTimeout)
Network requests

4. What is Async/Await?

async/await is a modern way to handle Promises.
It makes asynchronous code look like synchronous code, which improves readability.

async → makes a function return a promise
await → pauses execution until the promise resolves

```javascript
async function getUsers() {
  try {
    const response = await fetch("https://jsonplaceholder.typicode.com/users");
    const data = await response.json();

    console.log(data);
  } catch (error) {
    console.log(error);
  }
}

getUsers();
```
5. Difference Between Promise and Async/Await
```sql
| Feature        | Promise                  | Async/Await         |
| -------------- | ------------------------ | ------------------- |
| Syntax         | `.then()` and `.catch()` | `async` and `await` |
| Readability    | More complex             | Cleaner and easier  |
| Error Handling | `.catch()`               | `try...catch`       |
| Code Structure | Callback style           | Looks synchronous   |
| Introduced     | ES6                      | ES8                 |

```

6. What is the Event Loop in JavaScript?

The Event Loop is a mechanism that allows JavaScript to handle asynchronous operations while running on a single-threaded environment.

It continuously checks the call stack and task queue.
If the call stack is empty, the event loop moves tasks from the queue to the stack for execution.


Key Components

A.Call Stack
  Executes JavaScript functions.
  Works in Last In First Out (LIFO) order.
B. Web APIs / Browser APIs
  Handles async tasks like:
    setTimeout
    fetch
    DOM events
C.Callback Queue (Task Queue)
  Stores callbacks from async operations.
D.Event Loop
  Moves callbacks from the queue to the call stack when the stack is empty.
```javascript
console.log("1");

setTimeout(() => {
  console.log("2");
}, 0);

Promise.resolve().then(() => {
  console.log("3");
});

console.log("4");
1 → sync
4 → sync
3 → Promise (microtask queue)
2 → setTimeout (macrotask queue)
```

7. What is Prototype in JavaScript?

In JavaScript, every object has a hidden property called prototype.
It allows objects to inherit properties and methods from another object.

This concept is called Prototypal Inheritance.

```javascript
function Person(name) {
  this.name = name;
}
Person.prototype.sayHello = function () {
  console.log("Hello " + this.name);
};
const user1 = new Person("Gourab");
const user2 = new Person("Rahul");
user1.sayHello();
user2.sayHello();
Hello Gourab
Hello Rahul
```

Why Prototype is Used
  Memory efficient (methods shared between objects)
  Supports inheritance
  Helps create object-based relationships
  
8. What is Memoization?
Memoization is an optimization technique where the result of a function call is stored (cached) so that when the same input occurs again, the function returns the cached result instead of recalculating it.
This improves performance, especially for expensive computations.


```javascript
function square(n) {
  console.log("Calculating...");
  return n * n;
}

console.log(square(5));
console.log(square(5));
```
