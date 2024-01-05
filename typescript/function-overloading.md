TypeScript supports function overloading. Function overloading is the ability of a single function to have multiple type signatures and behaviors based on the arguments passed.

```typescript
function add(a: string, b: string): string;
function add(a: number, b: number): number;

function add(a: any, b: any): any {
  if (typeof a === 'string' && typeof b === 'string') {
    return a.concat(b);
  }

  if (typeof a === 'number' && typeof b === 'number') {
    return a + b;
  }

  throw new Error('Invalid argument types');
}

console.log(add('Hello, ', 'World!')); // "Hello, World!"
console.log(add(1, 2)); // 3
```

In this example, the `add` function has two overloads: one that takes two strings and returns a string, and another that takes two numbers and returns a number. The actual function implementation comes after the overload signatures, and it must be compatible with all of the overload signatures.

However, TypeScript's function overloading is not as flexible as in some other languages like Java or C#. TypeScript's function overloading is based on the number and types of arguments, but it doesn't support overloads that only differ by return type.