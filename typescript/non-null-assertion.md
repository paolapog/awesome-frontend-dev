**Non-null Assertion (`!`)**

The non-null assertion operator (`!`) is a postfix expression operator that can be used when the expression preceding it is not `null` or `undefined`. It tells TypeScript that the expression cannot be `null` or `undefined`, even if the type says it could be.

**Pros:**

1. **Bypasses Null Checks:** It allows you to bypass TypeScript's strict null checks.

2. **Simplifies Code:** It can make your code cleaner and easier to read when used appropriately.

**Cons:**

1. **Potential Runtime Errors:** If used incorrectly, it can lead to runtime errors. It tells TypeScript to assume a value is not `null` or `undefined`, but if it is at runtime, an error will occur.

2. **Bypasses Type Safety:** It bypasses one of TypeScript's safety checks, which can lead to bugs that are hard to track down.

**Use Cases:**

1. **When Value is Guaranteed to be Non-null:** It's useful when you know a value will not be `null` or `undefined`, but TypeScript's type checker cannot infer this.

2. **Working with DOM Elements:** It's often used when working with DOM elements and the `document.querySelector` method, which can return `null`.

**Best Practices:**

1. **Use Sparingly:** Only use the non-null assertion operator when you are absolutely sure that the value will not be `null` or `undefined`. Overuse can lead to runtime errors.

2. **Prefer Optional Chaining:** If you're not sure whether a value will be `null` or `undefined`, it's safer to use [optional chaining](../javascript/optional-chaining.md) (`?.`) instead. 
Optional chaining is a safer way to access nested properties, as it won't throw an error if a reference is `null` or `undefined`. Non-null assertion is a way to tell the compiler to bypass the null check, but it can lead to runtime errors if the value is actually `null` or `undefined`

**Examples:**

```typescript
// When value is guaranteed to be non-null
let value: number | null = getSomeValue();
let nonNullValue: number = value!; // OK

// Working with DOM elements
let element = document.querySelector('.my-class')!; // OK
element.style.color = 'red'; // OK
```

In these examples, the non-null assertion operator is used to tell TypeScript that `value` and `element` cannot be `null` or `undefined`. If they are `null` or `undefined` at runtime, an error will occur.