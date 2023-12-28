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