# Type Conversions

Type conversions in JavaScript can be implicitly coerced by the JavaScript engine or explicitly converted by the developer.

### String Conversion

String conversion can occur in the following cases:

- Explicit conversion using `String(value)`
- When outputted by stdout functions (except for Symbols)
- Concatenation with `+` when one of the operands is a string or an array (except for Symbols)
- Setting or accessing computed properties in objects (except for Symbols)
- Comparison using `==` between an object and a string

Examples of String conversion:

```javascript
String(true)    // "true"
String(null)    // "null"
String({})      // "[object Object]" unless .toString() or Symbol.toPrimitive is implemented
String([])      // ""
String([1,2,3]) // "1,2,3"
String(Symbol("my symbol")); // 'Symbol(my symbol)'
alert(Symbol("my symbol")); // Error! Cannot convert a Symbol value to a string
```

### Numeric Conversion

Numeric conversion can occur in the following cases:

- Mathematical functions and expressions
- Explicit conversion using `Number(value)`
- Unary `+` (not supported on BigInt)
- Comparisons between different types
- `isNaN`, `isFinite` functions (NOT `Number.isNaN`, `Number.isFinite`)
- `parseInt`, `parseFloat` functions

Examples of Numeric conversion:

```javascript
Number(undefined)     // NaN
Number(null)          // 0
Number(true)          // 1
Number(false)         // 0
Number("123")         // 123
Number("123abc")      // NaN
Number("")            // 0
Number({})            // NaN, unless .valueOf() or Symbol.toPrimitive is implemented
Number([])            // 0
Number([1,2,3])       // NaN
+'123'                // 123, unary plus
parseInt('10px')      // 10
parseFloat('10.5px')  // 10.5
```

Note: Comparisons can lead to unexpected conversions:

```javascript
1 < null      // false, null converts to 0
1 < "2"       // true, "2" converts to 2
1 < {}        // false, {} converts to NaN
"2" < {}      // false, {} converts to NaN
"10" < "2"    // true, lexicographic string comparison
```

### Boolean Conversion

Boolean conversion can occur in the following cases:

- During logical operations while evaluating
- Explicit conversion using `Boolean(value)`
- Result of condition in `if(...)` or ternary operator `?`
- Comparison using `==` between an object and a boolean

Examples of Boolean conversion:

```javascript
Boolean(0)               // false
Boolean(undefined)       // false
Boolean(null)            // false
Boolean(NaN)             // false
Boolean("")              // false
Boolean("0")             // true
Boolean({})              // true
Boolean([])              // true
Boolean(Symbol('hello')) // true
```

**Unusual Examples**

```javascript
"" + null + 0             // "null0", concatenation with a string
[] == ![]                 // true, both sides convert to 0
[] == []                  // false, different references
{} == {}                  // false, different references
"123" == new String("123") // true, object is converted to primitive
null == undefined         // true, special case
"0" == false              // true, both are converted to 0
"abc" == new Boolean(false) // false, string is not empty so it's truthy, Boolean object is truthy too, but they are different types
2 == [2]                  // true, array converts to primitive
```

### Comparison Operations and Type Conversions

When comparing values of different types, JavaScript performs a type conversion to compare the values:

- **Strict equality (`===`)** checks equality without type conversion. If the types differ, the values are considered unequal.

  Example:

    ```javascript
    0 === false; // false
    "0" === 0; // false
    ```

- **Loose equality (`==`)** checks equality with type conversion. If the types differ, JavaScript will attempt to convert one (or both) values to a common type before comparison.

  Example:

    ```javascript
    0 == false; // true
    "0" == 0; // true
    ```

For `undefined` and `null`, they are equal to each other but not to any other value:

```javascript
undefined == null; // true
null == 0; // false
undefined == 0; // false
```

For objects and primitives comparison:

- Objects are converted to primitives via their `toString` or `valueOf` methods (if implemented). If the conversion isn't possible, objects are not converted and checked for identity (same reference).
- If the comparison involves a string or a number, JavaScript tries to convert the object to these types (by calling the object's `toString` or `valueOf` methods).

For example:

```javascript
let obj = {valueOf: () => 100};
console.log(obj == 100); // true

let obj2 = {toString: () => "123"};
console.log(obj2 == "123"); // true
```
