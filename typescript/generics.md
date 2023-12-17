Generics are a way to make your code more **flexible** and **reusable**. They allow you to write code that can be used with **different types of data**, without having to write the same code over and over again. <br />
Generics also allow developers to create a component that can work with a variety of data types instead of a single one. This is useful when you want to create a component that can work with different types of data. <br/>
Let's have some __examples__ to understand the concept of generics:
```typescript
// A generic function named 'genericFn' that can work with any type 'T'.
function genericFn<T>(arg: T): T {
    return arg;
}

let output1 = genericFn<string>("myString");  // type of output will be 'string'
let output2 = genericFn<number>(100);  // type of output will be 'number'
```
```typescript
// A generic interface that describes a function.
interface UsefulFunction<T> {
    (input: T): T;
}

// The 'usefulFn' function implements the 'UsefulFunction' interface.
let myUsefulFunction: UsefulFunction<number> = usefulFn;
```
```typescript
// A generic class 'GenericNumber' that works with a set of types.
class GenericNumber<T> {
    zeroValue: T;
    add: (x: T, y: T) => T;
}

let myGenericNumber = new GenericNumber<number>();
myGenericNumber.zeroValue = 0;
myGenericNumber.add = function(x, y) { return x + y; };
```
```typescript
// A generic function 'getProperty' with a constraint that 'T' must have a property 'K'.
function getProperty<T, K extends keyof T>(obj: T, key: K) {
    return obj[key];
}

let x = { a: 1, b: 2, c: 3, d: 4 };
getProperty(x, "a"); // okay
getProperty(x, "m"); // error: Argument of type 'm' isn't assignable to 'a' | 'b' | 'c' | 'd'.
```
