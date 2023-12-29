In JavaScript, every function defines its own scope. Essentially, a scope is a **set of variables along with the principles that govern how these variables can be accessed by their names**. The variables scoped to a function are only accessible within that function. <br />

Within a given scope, each variable must have a unique name. Scopes can be nested within each other. If a scope is situated within another, the code within the inner scope can access variables from both the inner and outer scopes.

```javascript
function outer() {
  var x = 1; // x is in the local scope of outer
  function inner() {
    var y = 2; // y is in the local scope of inner
    console.log(x + y); // x can be accessed here because inner is nested inside outer, log: 3
  }
  inner();
  console.log(x + y); // ReferenceError: y is not defined
}
outer();
```

In the above example, the variable `x` is scoped to the function `outer`. The variable `y` is scoped to the function `inner`. The function `inner` can access the variable `x` because it is scoped to the function `outer`, which is the outer scope of `inner`. The function `outer` cannot access the variable `y` because it is scoped to the function `inner`, which is the inner scope of `outer`. <br />

JavaScript has the following kinds of __scopes__: <br/>
- __Global__ scope: The default scope for all code running in script mode.
- __Module__ scope: The scope for code running in module mode.
- __Function__ scope: The scope created with a function.
- __Block__ scope: The scope created with a block (with [let or const keyword](./let-const-var.md)).

## Global Scope
The global scope is the outermost scope of a JavaScript program. The global scope contains all the variables and functions that are not contained within a function. <br />

In the browser, the global scope is the `window` object. In Node.js, the global scope is the `global` object. <br />

Variables declared in the global scope are accessible from anywhere in the program. <br />

```javascript
var x = 1;
function foo() {
  console.log(x); // 1
}
foo();
console.log(x); // 1
```

In the above example, the variable `x` is declared in the global scope. The function `foo` can access the variable `x` because it is declared in the global scope. <br />

## Module Scope

The module scope is the scope created with a module. A module is a JavaScript file that is loaded with the `import` or `require` function. <br />

Variables declared in the module scope are accessible anywhere within the same module. If you want to access these variables in a different module, you need to export them from the original module and then import them in the module where you want to use them. <br />

```javascript

// module.js
export var x = 1;
function foo() {
  console.log(x); // 1
}
foo();
console.log(x); // 1
```

```javascript
// main.js
import { x } from './module.js';
console.log(x); // 1
```

## Function Scope

The function scope is the scope created with a function. <br />

Variables declared in the function scope are accessible anywhere within the same function. If you want to access these variables outside the function, you need to return them from the function. We have the example above to demonstrate this. <br />


## Block Scope

A block scope is the scope created with a block. A block is a set of statements enclosed within curly braces `{}`. <br />

Variables declared in the block scope are accessible anywhere within the same block. If you want to access these variables outside the block, you need to return them from the block. <br />

```javascript
{
  var x = 1; //var is not block scoped
  console.log(x); // 1
}
console.log(x); // 1
```

```javascript
{
  let x = 1;
  console.log(x); // 1
}
console.log(x); // ReferenceError: x is not defined
```

## Bonus Point: Lexical Scope
Lexical scope (also known as static scope) in JavaScript refers to the fact that every inner level can access its outer levels. There is a hierarchy of variables that is not affected by function invocation. This model is called lexical because it's based on __where variables and blocks of scope are authored, by you, at write (author) time__.

When a variable is used in JavaScript, the JavaScript engine will try to find the variable's value in the current scope. If it can't find it, it will look in the outer scope and will continue to do so up the scope chain until it either finds the variable or reaches the global scope.

```javascript
let globalVar = "I'm a global variable";

function outerFunction() {
  let outerVar = "I'm an outer variable";
  
  function innerFunction() {
    let innerVar = "I'm an inner variable";
    console.log(innerVar); // I'm an inner variable
    console.log(outerVar); // I'm an outer variable
    console.log(globalVar); // I'm a global variable
  }
  
  innerFunction();
}

outerFunction();
```
`innerFunction` has access to its own scope (where `innerVar` is defined), the outer function's scope (where `outerVar` is defined), and the global scope (where `globalVar` is defined). This is lexical scoping: the access to variables is determined by the position of the functions in the code, not by the order in which they are called.
