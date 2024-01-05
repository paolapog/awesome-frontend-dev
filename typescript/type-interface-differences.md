In TypeScript, both `type` and `interface` are used to describe the shape of an object or the type of a value. However, they have some differences and are used in different scenarios.

## Type

`type` is a way to provide a name for a type annotation. It's a powerful feature in TypeScript that allows you to compose types.

Pros:
- `type` is more powerful than `interface` because it supports more complex type definitions, such as union types, intersection types, mapped types, conditional types, etc.
- `type` can represent both object and primitive types.

Cons:
- `type` aliases are not as extendable as interfaces. You can't use an existing type alias to define new properties. You can create a new `type` that extends an existing one using intersection types. This allows you to add new properties to an existing `type`.

Use Cases:
- When you need to create complex type definitions.
- When you need to represent union or intersection types.
- When you need to represent primitive types.

```typescript
type Point = {
  x: number;
  y: number;
};

type D3Point = Point & {
  z: number;
};
```

## Interface

`interface` is a structure that defines the contract in your application. It defines the syntax for classes to follow.

Pros:
- Interfaces are extendable and can be merged using declaration merging. This means you can define an interface in multiple places and TypeScript will merge them together.
- Interfaces are more intuitive and easier to use for defining the shape of object types.

Cons:
- Interfaces can only represent the shape of object types. They can't be used to represent primitive types or to create complex type definitions.

Use Cases:
- When you need to define the shape of an object.
- When you need to define a contract for classes.
- When you need to extend or merge existing types.

```typescript
interface Point {
  x: number;
  y: number;
}

interface D3Point extends Point {
  z: number;
}
```