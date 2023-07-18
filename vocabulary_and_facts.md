# Vocabulary and facts

### Vocabulary

- **Exponentiation (a ** b)**: An operation that raises a number (a) to the power of another number (b).

- **Remainder (a % b)**: An operation that provides the remainder left after the division of `a` by `b`.

- **Operator precedence**: The hierarchy that determines how operators are parsed concerning each other.

- **Assignment operator (`=`)**: An operator that assigns a value to a variable.

- **Modify-in-place or modify-and-assign operators (+=, -= etc)**: Operators that change the value of a variable in place.

- **Postfix increment/decrement**: An operator that increments/decrements the value of a variable but returns the old value.

- **Prefix increment/decrement**: An operator that increments/decrements the value of a variable and returns the new value.

- **Comma operator**: An operator that evaluates multiple expressions and returns the result of the last one.

- **Conditional operator (`?:`)**: An operator that provides a shorter syntax for conditional statements.

- **Nullish coalescing operator (`??`)**: An operator that returns the right-hand side operand if the left-hand side operand is null or undefined.

- **Local variable**: A variable defined within a function or block, available only within that function or block.

- **Outer variable**: A variable that is defined outside of the current scope and is accessible inside the scope.

- **IIFE (Immediately-Invoked Function Expression)**: A JavaScript function that runs as soon as it is defined.

- **Derived class**: A class that is based on another class, termed the superclass.

- **Short-circuit evaluation**: Logical operators in JavaScript perform short-circuit evaluation.

- **Parentheses**: Parentheses can alter the order of operations in an expression, such as `1 + (1 + 2)`.

- **Scope & overshadow**: In JavaScript, a local variable will overshadow an outer variable with the same name.

- **Rest parameters & spread syntax**: In JavaScript, rest parameters are used to create functions that can take an unlimited number of arguments. The spread syntax allows an iterable to be expanded in places where zero or more arguments are expected.

- **Rethrowing errors**: In JavaScript, you can catch an error and throw it again using the `throw` statement.

### Facts

- **String comparison in JavaScript**: Strings in JavaScript are compared using the lexicographical order. Uppercase letters are considered less than lowercase ones.

- **NaN in comparisons**: NaN, when compared to any value, even itself, will return false.

- **Switch statement's equality checks**: The equality checks in switch statements in JavaScript use strict comparison (`===`).

- **Property value shorthand in objects**: In JavaScript ES6, if the key name is the same as the variable name, you can use a shorthand notation.

- **Array conversion in JavaScript**: Arrays in JavaScript convert to a string and then to any other types as needed.

- **Symbol usage in JavaScript**: Symbols can be used to add properties to objects in JavaScript that are hidden to most operations, and can't be directly accessed or altered.

- **Iteration order in Map and Set**: In JavaScript, the iteration order in Map and Set is the same as the insertion order.

- **Characteristics of WeakMap**: In JavaScript, a WeakMap doesn't prevent its keys from being garbage-collected. If there are no references to the key left, the key-value pair will be removed from the WeakMap.

- **Non-iterability of WeakMap and WeakSet**: In JavaScript, you can't iterate over the elements of a WeakMap or a WeakSet.

- **Fetch API's behavior**: The Fetch API in JavaScript returns a promise that resolves to the Response to the request, whether it is successful or not. The actual download of the resource starts as soon as the request is made, and the promise will resolve as soon as the headers have been received.
