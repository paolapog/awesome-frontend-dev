Prototypal inheritance is a form of object-oriented programming in JavaScript where __objects can inherit__ properties and methods from other objects. This is done through what's known as the prototype chain.

```javascript
function Person(name) {
  this.name = name;
}

Person.prototype.sayHello = function() {
  console.log(`Hello, my name is ${this.name}`);
}

let john = new Person('John');
john.sayHello(); // "Hello, my name is John"
```

`sayHello` is a method on `Person`'s prototype. When we call `john.sayHello()`, `this` inside `sayHello` refers to `john`. <br />

Take in mind that the end of every prototype chain is `null`. When an object's prototype is `null`, it means that the object does not inherit from any other object.

```javascript

let obj = Object.create(null); // Create an object with no prototype
console.log(Object.getPrototypeOf(obj)); // null
```

`Object.create(null)` creates a new object with no prototype. When we log the prototype of `obj` using `Object.getPrototypeOf(obj)`, the output is `null`, indicating that `obj` does not inherit from any other object.

This is an important aspect of the prototype chain in JavaScript. When looking up properties on an object, JavaScript will traverse the prototype chain until it either finds the property or reaches an object with a `null` prototype. If it reaches null, it means the property does not exist on the object or any of its prototypes, and undefined is returned.
To traverse the prototype chain, JS will look on `__proto__` property of the object. This property is a reference to the object's prototype. It's important to note that `__proto__` is not part of the prototype chain itself, but rather a way to access the prototype of an object.

```javascript
function Person(name) {
  this.name = name;
}

Person.prototype.sayHello = function() {
  console.log(`Hello, my name is ${this.name}`);
}

let john = new Person('John');

console.log(john.__proto__ === Person.prototype); // true
```

In this example, `john.__proto__ `points to `Person.prototype`. This is how `john` has access to the `sayHello` method: JavaScript looks up the prototype chain to find it.

However, it's important to note that while `__proto__` __is used internally__ by the JavaScript engine to traverse the prototype chain, its direct use in code is generally discouraged due to the reasons mentioned in the previous responses. Instead, `Object.getPrototypeOf()` and `Object.setPrototypeOf()` should be used to interact with an object's prototype.

Also, keep in mind that the prototype of an object is different from the prototype property of a function. The prototype property of a function is the object that will be assigned as the prototype of instances created with that function when called as a constructor. The prototype of an object created with a constructor function is the object that was referenced by the prototype property of that constructor function at the time the object was created.

**Pros:**

- It's more memory efficient than classical inheritance because methods are defined once on the prototype, rather than being redefined for each instance.
- It allows for dynamic inheritance, where an object's prototype can be changed and the changes will be reflected in all objects that inherit from that prototype.

**Cons:**

- The prototype chain can be confusing to understand and work with, especially for developers coming from languages with classical inheritance.
- It can lead to unexpected results if not used carefully, especially when dealing with properties that are objects or arrays.