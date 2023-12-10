The infer keyword allows you **to deduce a type from another type within a conditional type**. <br/>

```typescript
type ReturnType<T> = T extends (infer R)[] ? R : T;

type t1 = ReturnType<number[]>; // Infer R from number[]

type t2 = ReturnType<string>; // Infer T from string
```

In the above example, the conditional type checks whether the type is an array. If it is, the type R is inferred from the array and returned. Otherwise, the type T is returned. <br/>
The infer keyword is often used in conjunction with the extends keyword. <br/>