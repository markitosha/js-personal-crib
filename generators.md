# Generators

A generator is a special type of function in JavaScript that can pause its execution and then continue where it left off. It's defined with the `function*` syntax and uses the `yield` keyword to produce a sequence of values.

### Key Concepts

- Generators return multiple values: Unlike regular functions, generators can return ("yield") multiple values one after another, on a per-request basis.
- Generator function: A generator function is defined with `function*` syntax.
- Yield: `yield` keyword is used in the generator function body to specify the values to be returned from the generator.
- `next()` method: After calling `next()` on a generator function, it returns an object with the properties `value` (the yielded value) and `done` (a boolean indicating whether the generator has yielded its last value).
- For..of: Generators can be used with the `for..of` loop to iterate over the yielded values. However, `for..of` won't return the last value when `done` is true. To fix this, we need to return all values using `yield`.
- `yield*`: It can delegate execution to another generator.
- Passing values with `next()`: We can send values back into the generator using the `next(value)` method. The value passed to `next()` is treated as the result of the last `yield` expression.
- Async generators: Async generators can be used for handling data that is loaded in chunks, allowing the asynchronous loading of additional data while the previous data is being processed.

### Example

```javascript
function* idGenerator() {
  let id = 0;
  while (true) {
    yield id++;
  }
}

const generator = idGenerator(); 

console.log(generator.next().value); // 0
console.log(generator.next().value); // 1
console.log(generator.next().value); // 2
```
In this example, `idGenerator` is an infinite generator that yields a new id each time its `next` method is called.