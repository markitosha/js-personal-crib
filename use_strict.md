# Use strict

The "use strict" directive was introduced in ECMAScript 5 (ES5). It's a way to opt in to a restricted variant of JavaScript which does not allow certain actions and throws more exceptions.

### Enabling "use strict" mode:
- Placed at the top of a JavaScript file, it applies to the entire script.
- Placed at the beginning of a function, it applies only to that function.
- "use strict" mode is automatically enabled within ECMAScript 6 (ES6) `classes` and `modules`.

Here's a comparison table illustrating the differences:

| Scenario | Non-strict Mode | Strict Mode |
|---|---|---|
| Assigning to undeclared variable, read-only global property, or read-only declared variable | Allowed, no error | SyntaxError |
| `this` value outside any function | Global object | `undefined` |
| Function declaration within a block | Visible outside the block | Visible only inside the block |
| Deleting variables, function, or function parameters | Allowed, no error | SyntaxError |
| Changing a non-allowed property descriptor | Allowed, no error | TypeError |