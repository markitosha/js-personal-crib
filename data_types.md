# Data Types

JavaScript has several built-in data types:

### Primitive Data Types

1. **Number:** Can be integers or floating-point numbers. Special numeric values include `Infinity`, `-Infinity`, and `NaN` (Not a Number).
    ```javascript
    let num = 42; // integer
    let floatNum = 42.0; // floating point
    console.log(1 / 0); // Infinity
    console.log("not a number" / 2); // NaN
    ```

2. **BigInt:** Can represent integers larger than 2^53 - 1. The `n` at the end of the number signifies it's a BigInt.
    ```javascript
    const bigInt = 1234567890123456789012345678901234567890n;
    ```

3. **String:** Textual data, can be enclosed in single quotes (`'...'`), double quotes (`"..."`), or backticks (` `...` `). Backticks allow for embedded expressions.
    ```javascript
    let str1 = "Hello";
    let str2 = 'Hello again';
    let phrase = `Embedded ${str1}`;
    ```

4. **Boolean:** Represents a logical entity and can have two values: `true` or `false`.

5. **Null:** Represents the intentional absence of any object value.

6. **Undefined:** Represents an uninitialized variable.

7. **Symbol:** Represents a unique identifier. Symbols can be used as keys for object properties.

### Special Data Type

1. **Object:** A collection of properties. The properties are identified using key values.

Here's an example for Object and Symbol:

```javascript
let john = { name: "John", age: 30 }; // an object
let id = Symbol('id'); // a symbol
john[id] = "ID Value"; // assign a value to the symbol property
console.log(john[id]); // "ID Value"
```

The `typeof` operator can be used to determine the data type of a variable:

```javascript
typeof 10; // "number"
typeof "hello"; // "string"
typeof null; // "object" (this is considered a bug in JavaScript)
```

### Additional Concepts

- **Immutability:** Primitive values like numbers, strings, and booleans are immutable. This means that once a value is created, it can't be changed. However, variables assigned to these values can be changed to hold different values.

- **Built-in methods:** Many data types in JavaScript have built-in methods. For example, strings have methods like `at(N)`, `charAt(N)`, `concat(string)`, `indexOf(substring)`, etc. When a method is invoked on a primitive data type, JavaScript coerces the primitive value to an object, invokes the method on the object, and then discards the object.

- **Object Copying:** JavaScript objects are stored and copied by reference. Shallow copying of objects can be achieved with `Object.assign()`. For deep copying, one of the methods can be the `structuredClone` function (as of my knowledge cutoff in September 2021, `structuredClone` was still a proposal and not part of the ECMAScript standard).

```javascript
let obj = {a: 1, b: 2};
let shallowCopy = Object.assign({}, obj);
```

*Note:* Not directly related to data types, but there are two types of object properties: those with string keys and those with symbol keys. While a `for...in` loop will not return symbol properties, `Object.assign()` copies both string and symbol properties.