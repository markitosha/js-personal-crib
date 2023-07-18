# New

### How `new` Operator Works

1. **Creating an Empty Object**: When a function is called with `new`, the JavaScript engine creates a new empty object `{}`.

2. **Setting the Prototype**: The newly created object's prototype (`__proto__`) is set to the function's `prototype`.

3. **Executing the Function Body**: The function is called with the `this` keyword set to the newly created object. This allows the function to add properties and methods to `this` (the new object).

4. **Returning `this`**: If the function doesn't explicitly return a non-primitive value (object, array, function, or date), the `new` invocation will automatically return `this` (the new object).

Here's a step-by-step example:

```javascript
function Car(make, model) {
  this.make = make;
  this.model = model;
}

let myCar = new Car("Toyota", "Corolla");

console.log(myCar.make); // logs: "Toyota"
console.log(myCar.model); // logs: "Corolla"
```

In the above example, a new object is created, its prototype is set to `Car.prototype`, `Car` function is executed with `this` set to the new object, and finally, the new object is returned and assigned to `myCar`.

### Checking if a Function was Called with `new`

We can use the `new.target` property within a function to determine if the function was invoked using `new`. The `new.target` property is a reference to the constructor that was invoked with `new`. If the function wasn't invoked with `new`, `new.target` is `undefined`.

Here's an example:

```javascript
function Car(make, model) {
  if (!new.target) {
    console.log("Function was called without 'new'");
    return;
  }
  this.make = make;
  this.model = model;
}

let myCar = new Car("Toyota", "Corolla"); // logs nothing
let callWithoutNew = Car("Honda", "Civic"); // logs: "Function was called without 'new'"
```

In this example, when `Car` is called without `new`, `new.target` is `undefined` and a message is logged. When `Car` is called with `new`, `new.target` refers to `Car`, so the if statement is false and the function proceeds as usual.

### About `F.prototype`

Every function in JavaScript has a `prototype` property, which is an object. When a function is used as a constructor (i.e., called with `new`), the `[[Prototype]]` property of the newly created object is set to the function's `prototype` object. This means that the new object has access to the properties and methods defined on the function's `prototype`.

Example:

```javascript
function Car(make, model) {
  this.make = make;
  this.model = model;
}

Car.prototype.getMakeAndModel = function() {
  return this.make + " " + this.model;
}

let myCar = new Car("Toyota", "Corolla");
console.log(myCar.getMakeAndModel()); // logs: "Toyota Corolla"
```

In this example, `getMakeAndModel` method is added to the `Car.prototype`, and not directly in the `Car` function. This allows all instances of `Car` to access the `getMakeAndModel` method, as it's now part of their prototype chain.