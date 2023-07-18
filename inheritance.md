# Inheritance

- **Prototypal Inheritance**: In JavaScript, when a property is not found in an object, it will be searched for in the object's prototype, denoted by [[Prototype]] or `.__proto__`.

Example:

```javascript
let animal = {
  eats: true
};
let rabbit = {
  jumps: true,
  __proto__: animal
};
console.log(rabbit.eats); // logs: true
```

- **Property Iteration**: The `for...in` loop in JavaScript will iterate over an object's inherited properties.

- **Prototype Changing**: Modifying an object's prototype is typically not recommended. One of the few exceptions is for polyfilling native JavaScript functionality.

- **`F.prototype` and `new`**: When a function is used as a constructor with the `new` keyword, the `[[Prototype]]` of the created object is set to the `F.prototype`.

Example:

```javascript
function Rabbit(name) {
  this.name = name;
}
Rabbit.prototype.jumps = true;

let rabbit = new Rabbit("Roger");
console.log(rabbit.jumps); // logs: true
```

- **Inheriting with Functions**: If we inherit using functions, we need to not only set `F.prototype = Parent.prototype`, but also rewrite the constructor property: `F.prototype.constructor = F`.

Example:

```javascript
function Animal(name) {
  this.name = name;
}

Animal.prototype.eat = function() {
  console.log(this.name + ' eats.');
};

function Dog(name, breed) {
  Animal.call(this, name);  // inheriting "name" property
  this.breed = breed;
}

Dog.prototype = Object.create(Animal.prototype);  // inheriting methods
Dog.prototype.constructor = Dog;  // fixing the constructor reference

Dog.prototype.bark = function() {
  console.log(this.name + ' barks.');
};

let rex = new Dog('Rex', 'German Shepherd');

rex.eat();  // logs: "Rex eats."
rex.bark();  // logs: "Rex barks."
console.log(rex instanceof Animal);  // logs: true
console.log(rex instanceof Dog);  // logs: true
```

- **Class-based Inheritance**: In JavaScript classes, we use the `extends` keyword to denote inheritance. Any expression can follow `extends`, not necessarily a class.

Example:

```javascript
class Animal {
  eats() {
    return true;
  }
}
class Rabbit extends Animal {
  jumps() {
    return true;
  }
}
let rabbit = new Rabbit();
console.log(rabbit.jumps()); // logs: true
console.log(rabbit.eats()); // logs: true
```

- **Static Method Inheritance**: Built-in JavaScript classes do not inherit static methods.

- **`instanceof` Operator**: The `instanceof` operator checks an object's prototype chain. If the class has a static method `[Symbol.hasInstance]`, `instanceof` will use that method to check.

- **Checking Type**: You can use `{}.toString.call(object)` to check an object's type.

- **Mixin Creation**: If you want to create a mixin (a class that contains methods to be shared across multiple classes), you can use `Object.assign(Name.prototype, mixin)`. A mixin is a collection of behaviors that can be used by other classes.

Example:

```javascript
let sayHiMixin = {
  sayHi() {
    console.log(`Hello ${this.name}`);
  },
};
function User(name) {
  this.name = name;
}
Object.assign(User.prototype, sayHiMixin);

let user = new User("John");
user.sayHi(); // logs: "Hello John"
```