A variable of type ```any``` can be **assigned with anything**. <br/>

```typescript:
let a: any = 1;
a = "Hello";
a = true;
```
"In essence, by using ```any``` in TypeScript, you are essentially opting out of type checking. This means that the compiler allows any type of value to be assigned to a variable of type ```any``` without enforcing type constraints or providing type-related error checking. <br/>
If you want to use Typescript, you should avoid using ```any``` as much as possible. <br/>

When you declare a variable with the type ```unknown```, you can assign any value to it, similar to the ```any``` type. However, **when attempting to access a property** or value from this variable, TypeScript will generate an **error**. This error indicates that the property or value you are trying to access on a variable of the ```unknown``` type may not exist.

Using ```unknown``` requires you to incorporate a check before accessing any properties or values from a variable of this type, ensuring that the necessary validation is in place.
  
```typescript
let a: unknown = 30;
let b = a === 123; // boolean
let c = a + 10; // Error TS2571: Object is of type 'unknown'.
```
