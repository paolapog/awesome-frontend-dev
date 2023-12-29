In JavaScript, var, let, and const are used to declare variables, but they have some differences:

**var**: It is function-scoped when declared within a function. This means that it is available within the function it is declared in. If it is declared outside any function, it is globally scoped. var variables can be re-declared and updated.

**let**: It is block-scoped, meaning it is only available within the block it is declared in. let variables can be updated but not re-declared.

**const**: Just like let, const is also block-scoped. However, const variables can neither be updated nor re-declared. They must be initialized at the time of declaration.

Here is a simple example to illustrate the differences:

```javascript
for (var i = 0; i < 3; i++) {
  setTimeout(function() { console.log(i); }, 1000); // logs "3" three times
}

for (let j = 0; j < 3; j++) {
  setTimeout(function() { console.log(j); }, 1000); // logs "0", "1", "2"
}

const k = 10;
// k = 20; // TypeError: Assignment to constant variable.
console.log(k); // logs "10"
```

In the first loop, `var` is function-scoped, so there's only one i in the scope. By the time the `setTimeout` callbacks run, the loop has already finished and i is 3.

In the second loop, `let` is block-scoped, so each loop iteration has its own j. Each `setTimeout` callback refers to the j from its own loop iteration, so it logs the expected values.

const is also block-scoped, but it can't be reassigned after its initial assignment, so trying to reassign k results in a TypeError. <br />

## Benefits using let and const over var:

__Block Scope__: Unlike `var`, which is function-scoped, let and const are block-scoped. This means they exist only within the block they are defined in, which can help prevent variable leakage and unexpected behavior in your code.

__No Hoisting__: `var` variables are hoisted to the top of their scope and initialized with a value of undefined. let and const are also hoisted, but they are not initialized until their definition is evaluated. Accessing them before the initialization results in a **ReferenceError**.

__Immutable References__: `const` allows you to create references that can't be reassigned to a new value. This can be useful when you want to declare a variable that should always refer to the same value.

__Prevents Re-declaration__: `let` and `const` prevent re-declaring the same variable within the same scope, which can help catch errors.

Overall, `let` and `const` provide more control and help write cleaner and more predictable code, reducing the likelihood of bugs.

## Temporal Dead Zone (TDZ)
The Temporal Dead Zone (TDZ) is a behavior in JavaScript that occurs with `let` and `const` variables. It's the period between entering the [scope](./scope.md) where the variable is declared and the line where the declaration occurs. During this period, any reference to the variable will result in a ReferenceError.

Here's an example:

```javascript
function myFunc() {
  console.log(myVar); // ReferenceError: myVar is not defined
  let myVar = 2;
}

myFunc();
```

In this example, `myVar` is in the TDZ from the start of the function scope until the line where it's defined (`let myVar = 2;`). The attempt to access `myVar` in the `console.log` statement results in a ReferenceError because it's within the TDZ.

Kyle Simpson, in his book "You Don't Know JS: Scope & Closures", explains the TDZ as follows:

> "If a variable is accessed in its TDZ, a ReferenceError will be thrown. This error is usually seen when trying to access a variable before it's been declared. The TDZ ends once a variable has actually been declared, not assigned."

This means that the TDZ continues to exist until the variable declaration (not necessarily the assignment) is encountered in the code.