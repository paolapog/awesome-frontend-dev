Short-circuiting refers to the behavior of logical operators (`&&`, `||`, and `??`) where the second operand is only evaluated if the first operand does not definitively determine the result.

1. **Logical AND (`&&`):** If the first operand is falsy (a value which translates to `false` when evaluated in a boolean context, like `0`, `null`, `undefined`, `NaN`, `""`), the second operand is not evaluated, and the first operand is returned. If the first operand is truthy (a value which translates to `true` when evaluated in a boolean context), the second operand is evaluated and returned.

```typescript
let result = false && console.log("Hello"); // "Hello" is not logged because false is a falsy value
```

2. **Logical OR (`||`):** If the first operand is truthy, the second operand is not evaluated, and the first operand is returned. If the first operand is falsy, the second operand is evaluated and returned.

```typescript
let result = true || console.log("Hello"); // "Hello" is not logged because true is a truthy value
```

3. **Nullish Coalescing (`??`):** This operator is similar to the logical OR, but it only short-circuits if the first operand is `null` or `undefined` (not just any falsy value). If the first operand is `null` or `undefined`, the second operand is evaluated and returned. Otherwise, the first operand is returned.

```typescript
let result = null ?? "default"; // result is "default"
let result = 0 ?? "default"; // result is 0
```