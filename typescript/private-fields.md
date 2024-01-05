A private field in TypeScript is a special kind of class member that cannot be accessed from outside of the class it is defined in. This encapsulation ensures that the class has full control over how the field is used.

## Rules for Private Fields

1. **Naming Convention:** Private fields must start with a `#` character. This is the syntax that TypeScript uses to distinguish private fields from public ones.

```typescript
class MyClass {
  #myPrivateField: string;
}
```

2. **Accessibility:** Private fields are only accessible within the class body that they're declared in. They can't be accessed outside of the class or by subclasses.

```typescript
class MyClass {
  #myPrivateField: string;

  constructor() {
    this.#myPrivateField = "Hello, world"; // OK
  }
}

let instance = new MyClass();
console.log(instance.#myPrivateField); // Error: Property '#myPrivateField' is not accessible outside class 'MyClass' because it has a private identifier.
```

3. **Uniqueness:** Each private field name is unique to the class body it's declared in. If you have a subclass with the same private field name, it will be treated as a different field.

```typescript
class Parent {
  #myField: string;
}

class Child extends Parent {
  #myField: string; // This is a different field from the one in Parent
}
```

4. **Static and Instance Fields:** Private fields can be either instance fields or static fields. Instance fields are attached to instances of the class, while static fields are attached to the class itself.

```typescript
class MyClass {
  static #myStaticField: string;
  #myInstanceField: string;
}
```

5. **No Parameter Properties:** Unlike public, protected, and readonly properties, private fields cannot be declared as parameter properties in the constructor.

```typescript
class MyClass {
  constructor(private #myField: string) { } // Error: A parameter property may not be declared using a private name.
}
```

6. **No Compatibility with JavaScript Private Fields:** TypeScript's private fields are not compatible with the private fields in JavaScript (those declared with a `#` character). TypeScript private fields declared with the `private` keyword are not the same as JavaScript private fields declared with a `#` character.