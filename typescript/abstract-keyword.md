In TypeScript, the `abstract` keyword is used to define abstract classes and abstract methods.

**Abstract Classes:**

An abstract class is a base class from which other classes can be derived. They cannot be instantiated directly. Unlike an interface, an abstract class may contain implementation details for its members.

```typescript
abstract class Animal {
  abstract makeSound(): void;

  move(): void {
    console.log("Moving along...");
  }
}
```

**Abstract Methods:**

Abstract methods are methods within an abstract class that do not have an implementation in the abstract class, and instead, they must be implemented in any non-abstract child class.

```typescript
class Dog extends Animal {
  makeSound() {
    console.log('Bark');
  }
}
```

**Use Cases:**

1. **Defining Template Methods:** Abstract classes are great for defining template methods that provide a basic structure for an operation, and allow subclasses to fill in the details.

2. **Code Reuse:** Abstract classes can provide default behavior that can be shared among multiple subclasses.

**Pros:**

1. **Code Reuse:** Abstract classes allow you to define default behavior that can be shared among multiple subclasses.

2. **Enforcing Rules:** By using abstract methods, you can enforce certain rules that subclasses must follow.

**Cons:**

1. **Class Inheritance Limitations:** TypeScript does not support multiple class inheritance. A class can only extend a single class, abstract or not.

2. **Increased Complexity:** Abstract classes can increase the complexity of your codebase, as they add another layer of abstraction.

In conclusion, the `abstract` keyword in TypeScript allows you to define abstract classes and methods, which can be useful for enforcing certain rules and promoting code reuse. However, they also come with some limitations and can increase the complexity of your code.