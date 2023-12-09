TypeScript introduced the **never** type, signifying values that are never expected to occur.<br/>

This type is employed when there is a certainty that a particular scenario **will never materialize**. For instance, it is applicable when defining a function that either does not reach its endpoint or consistently throws an exception<br/>

```typescript   
// Example 1: Function with an infinite loop
function infiniteLoop(): never {
  while (true) {
    console.log('This loop runs forever.');
  }
}

// Example 2: Function that always throws an error
function alwaysThrowError(): never {
  throw new Error('This function always throws an error.');
}

// Example 3: Function with a switch statement covering all possible cases
type Fruit = 'Apple' | 'Banana' | 'Orange';

function exhaustiveCheck(fruit: Fruit): never {
  switch (fruit) {
    case 'Apple':
      // Do something for Apple
      break;
    case 'Banana':
      // Do something for Banana
      break;
    case 'Orange':
      // Do something for Orange
      break;
    default:
      // This block should never be reached
      const exhaustiveCheckError: never = fruit;
      throw new Error(`Unexpected fruit: ${exhaustiveCheckError}`);
  }
}

```
<br />

Difference between **never** and **void**:

The 'void' type can accommodate undefined or null as a value, while 'never' cannot have any value. Consider the following example:

```typescript
let someValue: void = undefined;
let noValue: never = undefined; // Error: Type 'undefined' is not assignable to type 'never'

//In TypeScript, a function declared with a return type of 'void' effectively returns undefined. Consider an alternative example:
function shoutHello(): void {
    console.log('Hello!');
}

let greeting: void = shoutHello();
console.log(greeting); // Result: undefined
```

As seen in this revised example, the variable greeting is assigned the value undefined, indicating that the ```shoutHello()``` function internally returns undefined, even though its declared return type is 'void'. Attempting to use the 'never' type for greeting would trigger a compile-time error, as 'void' is not assignable to 'never'.