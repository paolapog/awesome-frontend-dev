In TypeScript, `private` and `protected` are access modifiers that control the visibility of class members (properties and methods).

**Private:**

A `private` member is only accessible within the class that declares it.

```typescript
class MyClass {
  private myPrivateVar: string;

  constructor() {
    this.myPrivateVar = "Hello, world"; // OK
  }
}

let instance = new MyClass();
console.log(instance.myPrivateVar); // Error: Property 'myPrivateVar' is private and only accessible within class 'MyClass'.
```

**Protected:**

A `protected` member is accessible within the class that declares it and also within any class that extends (inherits from) that class.

```typescript
class MyClass {
  protected myProtectedVar: string;

  constructor() {
    this.myProtectedVar = "Hello, world"; // OK
  }
}

class MyChildClass extends MyClass {
  sayHello() {
    console.log(this.myProtectedVar); // OK
  }
}

let childInstance = new MyChildClass();
console.log(childInstance.myProtectedVar); // Error: Property 'myProtectedVar' is protected and only accessible within class 'MyChildClass' and its subclasses.
```
**Public:**
If no access modifier is specified for a member of a class, it is considered `public` by default. 

This means that the member is accessible everywhere, both within the class it's defined in, in classes that inherit from that class, and in any instances of that class.

Here's an example:

```typescript
class MyClass {
  myPublicVar: string; // This is public by default

  constructor() {
    this.myPublicVar = "Hello, world";
  }
}

let instance = new MyClass();
console.log(instance.myPublicVar); // "Hello, world"
```

In this example, `myPublicVar` is accessible outside of `MyClass` because it's `public` by default.

**Use Cases:**

1. **Private Members:** Use `private` when you want a class member to be completely hidden from outside code and subclasses. This is useful when you want to prevent external code from depending on internal details of a class, which allows you to change those details without affecting external code.

2. **Protected Members:** Use `protected` when you want a class member to be accessible to subclasses, but not to other external code. This is useful when you're designing a class to be extended, and you want subclasses to have access to certain properties or methods, but you still want to hide those members from other code.

3. **Public Members:** Public members are accessible from any location in the code. They are useful when you want to provide a public API for a class. This could include methods that should be called from outside the class, or properties that should be accessible for reading or writing. Public members define the interface that a class presents to the outside world.

