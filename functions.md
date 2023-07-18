# Functions

### Function Declaration vs Function Expression vs Arrow Function:

|          | Function Declaration | Function Expression | Arrow Function |
|:--------:|:--------------------:|:--------------------:|:--------------:|
|   Syntax   | function sum(a, b) { <br/> return a + b; <br/> } | let sum = function(a, b) { <br/> return a + b; <br/> }; | let sum = (a, b) => a + b; |
| Declaration | As a separate statement in the code. | Inside an expression or as a part of a complex expression. | Inside an expression or as a part of a complex expression. |
| Hoisting | Can be called before it is defined. | Cannot be called before it is defined. | Cannot be called before it is defined. |
| `this` Keyword | Refers to the context in which the function was called. | Refers to the context in which the function was called. | Does not have its own `this`. Instead, `this` is taken from the outer context. |
| `arguments` Variable | Available | Available | Not available |
| Usage with `new` | Can be used with `new` to construct new objects. | Can be used with `new` to construct new objects. | Cannot be used with `new`. |
| `super` Keyword | Available | Available | Not available |

### Function properties and methods

- `name`: This property returns the name of the function.
- `length`: This property returns the number of formal parameters in the function definition.
- `new Function`: This is a way to create a function from a string of code. However, it's generally not recommended due to security and performance concerns.
- Functions in JavaScript have their own lexical environment. If a function is defined in the global scope, it will only see the global lexical environment and won't have access to the outer one (if any).