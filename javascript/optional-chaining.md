Optional chaining is a feature in JavaScript that allows you to access deeply nested properties of an object without having to check for the existence of each level. It short-circuits (stops execution and returns `undefined`) if it encounters a `null` or `undefined` value.

**Pros:**

1. **Simplifies Code:** It reduces the need for repetitive null checks and makes your code cleaner and easier to read.

2. **Prevents Errors:** It helps prevent `TypeError` that would occur when trying to access a property of `null` or `undefined`.

**Cons:**

1. **Hidden Errors:** It might hide errors in some cases where `null` or `undefined` values are not expected.

2. **Return Value:** It always returns `undefined` when it fails, which might not be the desired behavior in all cases.

**Use Cases:**

1. **Accessing Nested Properties:** It's useful when you need to access a deeply nested property and you're not sure if all the intermediate levels exist.

2. **Calling Methods:** It can be used when calling a method which may not exist.

**Best Practices:**

1. **Don't Overuse:** While optional chaining can simplify your code, overusing it can lead to problems. If you're always expecting a property to exist, it's better to not use optional chaining. Unexpected `undefined` values can lead to harder-to-find bugs.

2. **Combine with Nullish Coalescing:** You can combine optional chaining with the nullish coalescing operator (`??`) to provide a default value when a property does not exist.

**Examples:**

```javascript
let user = {
  profile: {
    name: 'Alice',
    address: {
      street: '123 Main St',
      city: 'Wonderland'
    }
  }
};

// Accessing nested properties
let street = user?.profile?.address?.street; // '123 Main St'

// Calling methods
let length = user?.profile?.getName?.(); // undefined

// Combined with nullish coalescing
let city = user?.profile?.address?.city ?? 'Unknown'; // 'Wonderland'
```

In these examples, optional chaining is used to safely access properties and call methods. If any part of the chain is `null` or `undefined`, it short-circuits and returns `undefined`.