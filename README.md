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
