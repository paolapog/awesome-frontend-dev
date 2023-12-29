In JavaScript, when you define a function inside another function, the inner function has access to the variables in the outer function. This is due to JavaScript's [lexical scoping](./scope.md) rules, which state that a function has access to variables in its own scope and in any outer scopes.

A closure is created when the inner function __is made accessible outside__ of the function in which it was created. This can happen in various ways, such as by returning the inner function, storing it in a data structure, or passing it as an argument to another function.

The key characteristic of a closure is that __it retains access to the variables__ in the outer function's scope __even after__ the outer function __has finished executing__. This is possible because JavaScript functions carry a reference to their surrounding lexical scope, which includes any variables that were in scope at the time the function was created.

```javascript
function outerFunction(outerVariable) {
  return function innerFunction(innerVariable) {
    console.log('outerVariable:', outerVariable);
    console.log('innerVariable:', innerVariable);
  }
}

const newFunction = outerFunction('outside');
newFunction('inside'); // Logs: outerVariable: outside, innerVariable: inside
```

In this example, `innerFunction` is a closure that has access to `outerVariable`, even after `outerFunction` has finished execution.

**Pros:**

- Closures can be used to emulate private variables and methods, which can enhance code security and integrity.
- They allow for function factories and functional programming patterns.

**Cons:**

- Overuse of closures can lead to increased memory usage, as closed-over variables are not garbage collected as long as the closure exists.
- They can lead to confusion and complexity if not used carefully.

Kyle Simpson, in his "You Don't Know JS" series, has a lot to say about closures. Here are a couple of quotes:

> "Closure is when a function is able to remember and access its lexical scope even when that function is executing outside its lexical scope."

And:

> "Closures happen as a result of writing code that relies on lexical scope. They just happen. You do not even really have to intentionally create closures to take advantage of them. Closures are created and used all over your JavaScript code whether you realize it or not."

## Use Cases

1. **Data Privacy / Emulating Private Methods**: Closures can be used to emulate private methods, providing data privacy. This is useful when you want to hide implementation details and only expose an API to other parts of the code.

```javascript
function counter() {
  let count = 0;
  return function() {
    return ++count;
  };
}

const myCounter = counter();
console.log(myCounter()); // 1
console.log(myCounter()); // 2
```

In this example, `count` is not accessible directly from outside the `counter` function, providing a level of data privacy.

2. **Creating Function Factories**: A function factory is a function that returns another function, and the returned function can have access to the factory's scope.

```javascript
function multiplyBy(num) {
  return function(x) {
    return x * num;
  };
}

const multiplyByTwo = multiplyBy(2);
console.log(multiplyByTwo(4)); // 8
```

In this example, `multiplyBy` is a function factory. The function it returns has access to `num`.

3. **Event Handlers and Callbacks**: Closures are often used in event handlers and callbacks, where you need to preserve some data until the time the event handler or callback is invoked.

```javascript
let buttons = document.querySelectorAll('button');
for (let i = 0; i < buttons.length; i++) {
  buttons[i].addEventListener('click', function() {
    console.log('Button ' + i + ' clicked');
  });
}
```

In this example, each event handler forms a closure and has access to the `i` variable, preserving its value at the time the handler was created.

4. **Implementing Decorators, Middleware, or Higher-Order Functions**: Closures can be used to build more abstract functionality like decorators or middleware, which involve wrapping functions with additional behavior.

5. **Memoization**: Closures can be used to implement memoization, a technique used to speed up programs by storing the results of expensive function calls and reusing them when the same inputs occur again.