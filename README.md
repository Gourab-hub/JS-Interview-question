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
```sql
| Feature        | Promise           | Async/Await              |
| -------------- | ----------------- | ------------------------ |
| Syntax         | `.then().catch()` | `async / await`          |
| Readability    | More complex      | Cleaner                  |
| Error Handling | `.catch()`        | `try/catch`              |
| Usage          | Base concept      | Built on top of Promises |
```
