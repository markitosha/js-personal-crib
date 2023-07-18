# Variables

JavaScript provides three ways to declare variables: `var`, `let`, and `const`.

### Comparison: var vs let vs const
Sure thing, here's the expanded comparison table:

| Attribute | var | let | const |
|---|---|---|---|
| Scope | Function scope | Block scope | Block scope |
| Redeclaration | Allowed | Not allowed | Not allowed |
| Hoisting | Yes, initializes to `undefined` | Yes, but accessing before declaration results in ReferenceError | Yes, but accessing before declaration results in ReferenceError |
| Assignment without declaration | Allowed | Not allowed | Not allowed |
| Update value after declaration | Allowed | Allowed | Not allowed |
| Create property on global object when declared at global scope | Yes | No | No |
| Global Scope Attachment | Yes, becomes property of global object (`window` in browsers) when declared in global scope | No | No |
| Scope in Loop Statements | Single variable shared across loop iterations | New variable for each iteration | New variable for each iteration |
