In JavaScript, the `new` keyword is used to create an __instance of__ a user-defined __object type__ or of one of the built-in object types that has a constructor function.
A constructor is a special method in a class that gets called when a new object is created from that class. It's typically used to initialize the properties of the object. The `constructor` keyword is used to declare this method.

```javascript
function Person(name) {
  this.name = name;
}

let john = new Person('John');
console.log(john.name); // "John"
```

`new Person('John')` creates a new instance of `Person` with `name` set to 'John'.

`super` is a keyword in JavaScript that's used in the context of classes. It has two main uses:

1. In a constructor: When creating a class that extends another class, `super` is used to call the constructor of the parent class. This is necessary in order to properly set up the `this` object.

```javascript
class Employee extends Person {
  constructor(name, title) {
    super(name); // Call the constructor of the parent class (Person)
    this.title = title;
  }
}

let jane = new Employee('Jane', 'Engineer');
console.log(jane.name); // "Jane"
console.log(jane.title); // "Engineer"
```

In this example, `Employee` extends `Person`. In the `Employee` constructor, we call `super(name)` to run the `Person` constructor with the given name. This sets up `this.name` correctly. Then we can add additional properties like `this.title`.

2. In methods: `super` can also be used to call methods on a parent class.

```javascript
class Employee extends Person {
  constructor(name, title) {
    super(name);
    this.title = title;
  }

  greet() {
    return `${super.greet()} I'm an ${this.title}.`;
  }
}
```

In this example, `super.greet()` calls the `greet` method on the parent class (`Person`).

## Difference between: `function Person(){}`, `var person = Person()`, and `var person = new Person()`

1. `function Person() {}`: This is a function declaration. It defines a function named `Person`. This function can be invoked as `Person()` or used as a constructor with the `new` keyword as `new Person()`.

```javascript
function Person() {
  this.name = "John Doe";
}

console.log(typeof Person); // "function"
```

2. `var person = Person()`: This is a function invocation (**NOT** constructor invocation). It calls the function `Person` and assigns the result to the variable `person`. If `Person` doesn't explicitly return a value, `person` will be `undefined` because in JavaScript, a function without a return statement automatically returns `undefined`.

```javascript
// NON-STRICT MODE
function Person() {
  this.name = "John Doe";
  return this.name;
}

var person = Person();
console.log(person); // "John Doe" if in non-strict mode

// STRICT MODE
"use strict";
function Person() {
  this.name = "John Doe"; // TypeError: Cannot set property 'name' of undefined
  return this.name;
}

var person = Person(); // Uncaught TypeError: Cannot set property 'name' of undefined
console.log(person);
```
In JavaScript, the value of [this](./this-keyword.md) inside a function depends on how the function is called. 
In non-strict mode, if you call a function (not as a method or a constructor), `this` will be the global object (`window` in a browser). So, in the example, `this.name` will actually set a global variable `name`.
In strict mode, if you call a function (not as a method or a constructor), `this` will be `undefined`. So, `this.name` will throw a `TypeError`.

3. `var person = new Person()`: This is a constructor invocation. It creates a new object, sets the prototype of this object to `Person.prototype`, calls the `Person` function with `this` set to the new object, and assigns the new object to the variable `person`. If `Person` doesn't explicitly return an object, the new object created by `new` will be used as the result. This is how custom types are usually created in JavaScript.

```javascript
function Person() {
  this.name = "John Doe";
}

var person = new Person();
console.log(person.name); // "John Doe"
```