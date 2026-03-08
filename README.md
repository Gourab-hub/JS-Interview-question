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
9. What is Event Bubbling?

Event Bubbling is a mechanism where an event starts from the target element and then propagates upward to its parent elements in the DOM tree.
In simple terms, the event moves from child → parent → grandparent → document.

```html
<div id="parent">
  <button id="child">Click Me</button>
</div>
```

### JavaScript

```javascript
document.getElementById("parent").addEventListener("click", () => {
  console.log("Parent clicked");
});

document.getElementById("child").addEventListener("click", () => {
  console.log("Button clicked");
});
```

### When you click the button

### Output
```
Button clicked
Parent clicked
```
10.Call Stack vs Event Loop

Call Stack:
The call stack executes synchronous JavaScript code and function calls.

```javascript
function first() {
  second();
}
function second() {
  console.log("Hello");
}
first();
```
Event Loop:
The event loop moves asynchronous callbacks from the queue to the call stack when the stack becomes
```javascript
console.log("Start");

setTimeout(() => {
  console.log("Timeout");
}, 0);

console.log("End");
```
```sql
| Feature   | Call Stack         | Event Loop               |
| --------- | ------------------ | ------------------------ |
| Purpose   | Executes functions | Handles async tasks      |
| Type      | Data structure     | Mechanism                |
| Execution | Synchronous        | Asynchronous             |
| Role      | Runs code          | Moves callbacks to stack |

```
11. Promise vs Promise Chaining

A. What is a Promise?

A Promise is used to handle asynchronous operations in JavaScript.
It represents a value that may be available now, later, or never.
A promise has three states:
  Pending
  Resolved (Fulfilled)
  Rejected


```javascript
function getData() {
  return new Promise((resolve, reject) => {
    resolve("Data received");
  });
}

getData()
  .then((data) => {
    console.log(data);
  })
  .catch((error) => {
    console.log(error);
  });
```

B. What is Promise Chaining?

Promise Chaining means using multiple .then() methods in sequence to perform multiple asynchronous operations one after another.
```javascript
Promise.resolve(2)
  .then((num) => {
    console.log(num);
    return num * 2;
  })
  .then((num) => {
    console.log(num);
    return num * 2;
  })
  .then((num) => {
    console.log(num);
  });
```
```sql
| Feature   | Promise                     | Promise Chaining                               |
| --------- | --------------------------- | ---------------------------------------------- |
| Meaning   | Handles one async operation | Handles multiple async operations sequentially |
| Syntax    | `.then()`                   | Multiple `.then()`                             |
| Usage     | Single task                 | Series of dependent tasks                      |
| Data Flow | One result                  | Result passed to next `.then()`                |

```
12. What is a Function Expression?

A Function Expression is a function that is assigned to a variable.
Unlike function declarations, function expressions are not hoisted, so they cannot be used before they are defined.

```javascript
const greet = function() {
  console.log("Hello");
};
greet();//Hello
```
13. Function Declaration vs Function Expression
```javascript
greet();

function greet() {
  console.log("Hello");
}
//Hello
```
```javascript
greet();

const greet = function () {
  console.log("Hello");
};
//ReferenceError: Cannot access 'greet' before initialization
```
```sql
| Feature                | Function Declaration              | Function Expression           |
| ---------------------- | --------------------------------- | ----------------------------- |
| Definition             | Declared using `function` keyword | Function assigned to variable |
| Hoisting               | Yes                               | No                            |
| Call before definition | Possible                          | Not possible                  |
| Use case               | General functions                 | Callbacks, closures           |

```
14. var vs let vs const

```sql
| Feature   | var      | let       | const     |
| --------- | -------- | --------- | --------- |
| Scope     | Function | Block     | Block     |
| Redeclare | Yes      | No        | No        |
| Update    | Yes      | Yes       | No        |
| Hoisting  | Yes      | Yes (TDZ) | Yes (TDZ) |
```
15.What is the Rest Operator?

The Rest Operator (...) allows a function to collect multiple arguments into a single array.
It is mainly used when the number of arguments passed to a function is unknown.

```javascript
function sum(...numbers) {
  return numbers.reduce((total, num) => total + num, 0);
}
console.log(sum(1, 2, 3));
console.log(sum(4, 5, 6, 7));
```
16. What is Shallow Copy?
A Shallow Copy creates a new object, but nested objects still reference the original object.
So if you change a nested value, it affects the original object.

```javascript
const user = {
  name: "Gourab",
  address: {
    city: "Kolkata"
  }
};

const copyUser = { ...user };
copyUser.address.city = "Delhi";
console.log(user.address.city);
```
17. What is Deep Copy?
A Deep Copy creates a completely independent copy, including all nested objects.

Changes in the copied object do not affect the original object.
```javascript
const user = {
  name: "Gourab",
  address: {
    city: "Kolkata"
  }
};

const deepCopy = JSON.parse(JSON.stringify(user));
deepCopy.address.city = "Delhi";
console.log(user.address.city);
```
18. Difference Between Shallow Copy and Deep Copy
```sql
| Feature     | Shallow Copy                   | Deep Copy                      |
| ----------- | ------------------------------ | ------------------------------ |
| Copy Level  | First level only               | All nested levels              |
| Reference   | Nested objects share reference | No shared reference            |
| Performance | Faster                         | Slower                         |
| Example     | `Object.assign()` / Spread     | `JSON.parse(JSON.stringify())` |
```
