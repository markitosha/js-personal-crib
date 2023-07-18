# Promises

- **Settled Promise**: A Promise whose outcome is already determined.
- **Pending Promise**: A Promise whose outcome is not yet determined.
- **Executor**: The function passed to the `new Promise` constructor. It contains the instructions for the Promise.
- **Promise Chaining**: A technique where `.then` or `.catch` methods return a new promise, allowing these methods to be chained together.
- **Unhandled Rejection**: An event that is triggered when a Promise is rejected, but no error handler is attached to handle it.

Example:
```javascript
let promise = new Promise((resolve, reject) => {
  setTimeout(() => resolve("Done!"), 1000);
});

promise.then(
  result => console.log(result),  // "Done!"
  error => console.log(error)     // Doesn't run
);
```

### Async/Await

- Async: A keyword that makes a function return a Promise.
- Await: A keyword that makes JavaScript wait until that Promise settles and returns its result.


Example:
```javascript
async function asyncFunc() {
  let response = await fetch('https://api.github.com/users');
  let users = await response.json();
  console.log(users[0].login);
}

asyncFunc();  // Output: First username from GitHub users API
```

### Key Differences

- Async/await syntax is cleaner and more readable compared to promise chains.
- Error handling in async/await can be done using a single try/catch block, while promises require a `.catch` at each level.
- Async/await makes it easier to debug with step-through debugging.
- Unlike Promises, async/await makes it easy to store the resolved value in a variable directly.