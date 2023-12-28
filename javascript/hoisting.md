Hoisting is a JavaScript mechanism where variables and function declarations are moved to the top of their containing scope during the compile phase, before the code has been executed. It's important to note that **only the declarations** are hoisted, not initializations.

```javascript
// Calling the function before it's defined in code
console.log(greet("John")); // "Hello, John"

// Function declaration
function greet(name) {
  return "Hello, " + name;
}
```

The function `greet` is hoisted to the top of the scope, which allows us to call it before it's defined in the code. This is a key feature of function hoisting. Note that this behavior applies to function declarations, not function expressions.

Function expressions:

```javascript
// Trying to call the function before it's defined in code
console.log(greet("John")); // TypeError: greet is not a function

// Function expression
var greet = function(name) {
  return "Hello, " + name;
};
```

In this case, the variable `greet` is hoisted, but its assignment as a function happens at runtime, not compile time. So trying to call `greet` before its definition results in a TypeError.

**Pros:**

- It allows you to call functions before they appear in your code.

**Cons:**

- It can cause confusion and bugs because variables can be used before they are declared.