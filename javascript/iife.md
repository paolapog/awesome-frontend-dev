An Immediately Invoked Function Expression (IIFE) is a JavaScript __function that runs as soon as it is defined__. The syntax looks like this:
```javascript
(function() {
  // statements
})();
```

Or with arrow functions:
```javascript
(() => {
  // statements
})();
```

IIFEs are useful for **protecting** the [scope](./scope.md) of your functions and variables. Everything defined inside the IIFE **is not accessible** from the outside world, so it won't pollute the global scope. This is helpful when you want to isolate parts of your code to prevent naming conflicts.

Here's an example:
```javascript
(function() {
  var privateVar = "I am private";
  console.log(privateVar); // "I am private"
})();


console.log(privateVar); // Uncaught ReferenceError: privateVar is not defined
```

In this example, `privateVar` is not accessible outside the IIFE, so trying to log it outside the IIFE results in a ReferenceError.

You should use IIFEs when you want to create a new scope that doesn't pollute the global scope. This is especially useful in large codebases where naming conflicts can be a problem.

However, you should not use IIFEs when you want to create functions or variables that need to be reused in different parts of your code. Since IIFEs isolate their contents from the outside world, anything defined inside an IIFE __cannot be accessed from outside it__.


## Common use cases for IIFEs in details
1. **Module Creation**: IIFEs are often used to create modules. The variables and functions are encapsulated within the IIFE, and only a public API is returned to be accessed from the outside.
  ```javascript
  var myModule = (function() {
    var privateVar = "I am private";
    
    return {
      publicMethod: function() {
        console.log(privateVar);
      }
    };
  })();

  myModule.publicMethod(); // "I am private"
  ```


2. **Avoiding Global Scope Pollution**: IIFEs are used to avoid declaring variables in the global scope, preventing potential naming conflicts.
  ```javascript
  (function() {
    var temp = "I am temporary";
    console.log(temp); // "I am temporary"
  })();

  console.log(temp); // Uncaught ReferenceError: temp is not defined
  ```


3. **Creating Fresh Environments**: IIFEs can be used to create a fresh environment for each iteration in a loop, especially useful when working with asynchronous code.
  ```javascript
  for (var i = 0; i < 5; i++) {
    (function(i) {
      setTimeout(function() {
        console.log(i); // Will output the number at the specific iteration
      }, i * 1000);
    })(i);
  }
  ```

4. **Private State: With IIFEs**, you can create functions with a persistent private state. This is the basis of the module pattern, where you can create a function that returns an object with methods that can access and modify the private state.
  ```javascript
  var counter = (function() {
    var privateCounter = 0;
    return {
      increment: function() {
        privateCounter++;
      },
      decrement: function() {
        privateCounter--;
      },
      value: function() {
        return privateCounter;
      }
    };
  })();

  console.log(counter.value()); // 0
  counter.increment();
  counter.increment();
  console.log(counter.value()); // 2
  counter.decrement();
  console.log(counter.value()); // 1
  ```