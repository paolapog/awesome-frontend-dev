In TypeScript, a const assertion is a type of assertion that tells the compiler to infer the most literal type possible for a variable. It's done by appending `as const` to the end of the expression. Here are some use cases:

**1. Immutable Arrays:**

If you want to create a readonly tuple, you can use a const assertion. The inferred type will be a readonly tuple, not an array, and the length of the array will be part of the type.

```typescript
const arr = [10, 20] as const;
// inferred type: readonly [10, 20]
```

**2. Immutable Objects:**

If you want to create an object with readonly properties, you can use a const assertion. The inferred type will have readonly properties.

```typescript
const obj = { x: 10, y: 20 } as const;
// inferred type: { readonly x: 10; readonly y: 20; }
```

**3. Enum-like Behavior:**

If you want to create a group of related constants, you can use a const assertion with an object. This can be a lightweight alternative to [enums](./enums.md).

```typescript
const Directions = {
  Up: 'UP',
  Down: 'DOWN',
  Left: 'LEFT',
  Right: 'RIGHT',
} as const;

let dir: keyof typeof Directions = Directions.Up;
```

In all these cases, the const assertion prevents you from changing the values once they are set, and it also gives you a more precise type. It's a powerful tool for creating immutable data structures and for working with literal types.