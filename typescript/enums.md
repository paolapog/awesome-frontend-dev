Enums in TypeScript allow developers to define a set of named constants, which can be either numeric or string-based. This can simplify code and make it easier to document intent.

```typescript
enum Direction {
  Up,
  Down,
  Left,
  Right,
}
```

The above TypeScript enum compiles to the following JavaScript:

```javascript
var Direction;
(function (Direction) {
    Direction[Direction["Up"] = 0] = "Up";
    Direction[Direction["Down"] = 1] = "Down";
    Direction[Direction["Left"] = 2] = "Left";
    Direction[Direction["Right"] = 3] = "Right";
})(Direction || (Direction = {}));
```

This code creates a bidirectional mapping from strings to numbers and vice versa, which can be useful for debugging or logging.

String enums are similar, but each member must be initialized with a string literal or another string enum member.

```typescript
enum Direction {
  Up = "UP",
  Down = "DOWN",
  Left = "LEFT",
  Right = "RIGHT",
}
```

While it's possible to create mixed enums with both string and numeric members, it's generally not recommended due to potential confusion and type inconsistency.

Enums can also be declared without generating any actual code, which can be useful when working with libraries like jQuery where you want type information but don't need any code to be produced. This is known as an "ambient" context.

```typescript
declare enum Example {
  A = 1,
  B, // Error! 'B' is not constant-initialized, so it is considered computed
}
```

For performance and code size reasons, references to enum members are often replaced with their numeric equivalents during compilation, a process known as "inlining". This only happens when the compiler can guarantee that the enum member is a constant.

```typescript
enum Colors {
  Red = 1,
  Green = 2,
  Blue = 3
}

const selectedColor = Colors.Green;
// TypeScript might emit: "const selectedColor = 2;" during compilation
```

Enum members can be either computed (value not known at compile-time) or non-computed (value known at compile-time). References to non-computed members are always inlined, while references to computed members cannot be.

If an enum declaration has the `const` modifier, all references to its members are inlined. This can be useful when you want to avoid the cost of generating the enum object at runtime.

```typescript
const enum Colors {
  Red = 1,
  Green = 2,
  Blue = 3
}

const selectedColor = Colors.Green;
// TypeScript will always emit: "const selectedColor = 2;" 
```

A `declare enum` will not emit an object, and references to its members are inlined if those members are computed. A `declare const enum` behaves the same as a `const enum`, except that non-declare const enums will emit an object when the `--preserveConstEnums` flag is used. This can be useful for debugging.

In terms of use cases, enums are great for representing a fixed set of related values, like directions, days of the week, or colors. They can make your code more readable and less error-prone by replacing magic numbers or strings with meaningful identifiers.

However, enums in TypeScript have some downsides. They can add complexity and potential confusion, especially when used with string values or mixed types. They also don't align perfectly with JavaScript, which doesn't have a native enum type, leading to potential confusion when working with compiled code or JavaScript libraries. Finally, the inlining behavior of enums can lead to unexpected results if you're not aware of it.

Reference: https://stackoverflow.com/questions/28818849/how-do-the-different-enum-variants-work-in-typescript

Please, be aware that you may not need an enum when an object with as const could suffice. 