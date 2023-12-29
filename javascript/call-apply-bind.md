In JavaScript, `call`, `apply`, and `bind` are methods associated with functions. They are used to control the [this](./this-keyword.md) context of the function invocation. `call` and `apply` are quite similar as they both invoke the function immediately, but they differ in how they accept arguments. On the other hand, `bind` does not invoke the function immediately but returns a new function with a specified `this` context and arguments.

**call**: The `call` method calls a function with a given `this` value and arguments provided individually.

```javascript
function greet(arg1, arg2) {
  console.log(`${this.name} says ${arg1} and ${arg2}`);
}

const obj = { name: 'John' };

greet.call(obj, 'Hello', 'Goodbye'); // John says Hello and Goodbye
```

**apply**: The `apply` method calls a function with a given `this` value and arguments provided as an array (or an array-like object).

```javascript
function greet(args) {
  console.log(`${this.name} says ${args[0]} and ${args[1]}`);
}

const obj = { name: 'John' };

greet.apply(obj, ['Hello', 'Goodbye']); // John says Hello and Goodbye
```

**bind**: The `bind` method creates a new function that, when called, has its `this` keyword set to the provided value, with a given sequence of arguments preceding any provided when the new function is called.

```javascript
function greet(arg1, arg2) {
  console.log(`${this.name} says ${arg1} and ${arg2}`);
}

const obj = { name: 'John' };

let boundGreet = greet.bind(obj, 'Hello', 'Goodbye');
boundGreet(); // John says Hello and Goodbye
```

**Pros**:

- `call`, `apply`, and `bind` allow you to control the context of function execution, meaning you can manipulate the `this` value inside the function.
- They can be used for borrowing methods from other objects.
- `bind` allows for function currying, where a function with multiple arguments is transformed into a sequence of functions each with a single argument (or a subset of arguments).

**Cons**:

- `call`, `apply`, and `bind` can make code harder to understand and debug due to dynamic `this` context.
- They are slower than a direct function invocation.
- Unlike `call` and `apply`, `bind` does not immediately invoke the function but instead returns a new function, which might not be the desired behavior in all cases.

Kyle Simpson, in his "You Don't Know JS", about `call`, `apply` and `bind`:

> "Hard-bound functions are not only useful for callbacks. You can also use them to create functions that have some of the arguments pre-specified. This is often called partial application."

> "The bind(..) utility creates a new function that will force the call site's this to be what you want it to be, even if the function is invoked with a normal function call."