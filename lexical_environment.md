# Lexical Environment

- **Environment Record**: Special object with all local variables in a code block.
- **Outer Reference**: Each record refers to its outer environment, creating a chain of scopes.
- **Function Declarations**: Fully defined upon entering its context, they can be used before they're defined.
- **Variable Lookup**: Starts from the current environment record and moves to outer environments until the global scope.

Example:

```javascript
let a = 1;
function outer() {
  let b = 2;
  function inner() {
    let c = 3;
    console.log(a, b, c);
  }
  inner();
}
outer();
```

### Closure

- A closure is a function that can access and remember its outer variables, even after the outer function has finished execution.

Example:

```javascript
function outer() {
  let outerVar = "I'm outer variable";
  function inner() {
    console.log(outerVar);
  }
  return inner;
}
let myClosure = outer();
myClosure(); // logs: "I'm outer variable"
```