Structural typing is a way of checking types that is fundamentally different from the more common nominal typing used in languages like Java or C#. 

In a nominal typing system, two variables are type-compatible if and only if their declarations name the same type. For example, if you have a class `Dog` and a class `Cat`, a variable of type `Dog` cannot be assigned a `Cat` object, because `Dog` and `Cat` are different types, even if they have exactly the same properties and methods.

```java
class Dog {
  String name;
}

class Cat {
  String name;
}

Dog dog = new Dog();
Cat cat = new Cat();

// This would be a type error in a nominal typing system
dog = cat; 
```

In contrast, TypeScript uses a structural typing system. In a structural typing system, two variables are type-compatible if their types are structurally compatible, regardless of what they are named. So if you have a `Dog` interface and a `Cat` class in TypeScript, and they both have a `name` property of type `string`, you can assign a `Cat` object to a variable of type `Dog`.

```typescript
interface Dog {
  name: string;
}

class Cat {
  name: string;
}

let dog: Dog;
let cat = new Cat();

// This is OK in TypeScript's structural typing system
dog = cat; 
```

In this example, even though `Cat` doesn't explicitly implement `Dog`, TypeScript considers `Cat` to be compatible with `Dog` because they have the same structure: they both have a `name` property of type `string`.

So, in essence, structural typing is about checking the shape or structure of the data, not the specific type names. This provides a lot of flexibility, but it also requires you to be careful to ensure your data structures match up as expected.

**Use Cases:**

1. **Flexible APIs:** Structural typing allows you to create flexible APIs that accept any object that has certain properties, regardless of its actual class or interface.

2. **Mocking in Tests:** Structural typing makes it easy to create mock objects in tests. You can create an object that has the same structure as the object you're mocking, without having to create a subclass or implement an interface.

**Pros:**

1. **Flexibility:** Structural typing provides a lot of flexibility. You can pass an object to a function if the object matches the structure that the function expects.

2. **Ease of Use:** It's easy to create objects that conform to an interface without having to explicitly implement the interface.

**Cons:**

1. **Lack of Explicitness:** With structural typing, it's not always clear which interfaces a class is intended to implement. This can make the code harder to understand.

2. **Potential for Errors:** Because TypeScript uses structural typing, it's possible to accidentally pass an object to a function that happens to have the right structure, but isn't actually the right kind of object. This can lead to subtle bugs.