In TypeScript, `unique symbol` is a subtype of [symbol](../javascript/symbol.md) that can only be assigned to a `const` variable or a `readonly` property. The purpose of `unique symbol` is to create a symbol that is guaranteed to be unique across your entire program.

```typescript
const MySymbol = Symbol() as unique symbol;
```

## Best practices and use cases:

**1. Use Symbols for Unique Property Keys:**

Symbols are great for creating unique property keys that won't collide with other properties. This can be useful when you're adding properties to objects dynamically and want to avoid overwriting existing properties.

```typescript
const uniqueKey = Symbol();
let obj = {};
obj[uniqueKey] = "value";
```

**2. Use `unique symbol` for Absolute Uniqueness:**

If you need a symbol that is guaranteed to be unique across your entire program, use `unique symbol`. This can be useful for tagging values or implementing certain data structures.

```typescript
const uniqueKey = Symbol() as unique symbol;
```

**3. Use Descriptions for Debugging:**

When you create a symbol, you can provide a description. This description is not used as part of the uniqueness check, but it can be useful for debugging.

```typescript
const mySymbol = Symbol("my symbol");
```

**4. Be Aware of Coercion:**

Symbols cannot be automatically coerced to a string or number. If you try to do this, you'll get a runtime error. If you need to convert a symbol to a string, you can use the `toString` method.

```typescript
const mySymbol = Symbol("my symbol");
console.log(String(mySymbol)); // "Symbol(my symbol)"
```

**5. Use Symbols Sparingly:**

Symbols can be powerful, but they can also make your code harder to understand if used excessively. Use them sparingly and only when necessary.

**6. Singleton Patterns:**

`unique symbol` can be used in the implementation of the Singleton pattern, where you want to ensure that a class has only one instance.

Remember, symbols are not enumerable in a standard `for...in` loop or `Object.keys()`, so they can be a good choice when you want to hide properties from these operations.