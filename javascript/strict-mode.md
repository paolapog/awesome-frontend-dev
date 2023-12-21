Introduced in __ECMAScript 5__, strict mode imposes more rigorous parsing and error handling on your code at runtime. It also helps you write cleaner code and catch errors and bugs that might otherwise go unnoticed.
You can enable it with `use strict` at the beginning of a file, a program, or a function body. Strict mode applies to the entire script or function body. It doesn't apply to block statements enclosed in {} braces.

## Benefits of strict mode
1. Prevent accidental creation of global variables
  ```javascript
  function foo() {
      "use strict";
      x = 10; // ReferenceError: x is not defined
  }
  foo();
  ```

2. Prevents you from using words that are reserved for future versions of JavaScript
  ```javascript
  function foo() {
      "use strict";
      var implements = 10; // SyntaxError: Unexpected reserved word
  }
  foo();
  ```

3. Prevents you from using duplicate names for parameters
  ```javascript
  function foo(a, b, a) {
      "use strict";
      console.log(a, b, a); // SyntaxError: Duplicate parameter name not allowed in this context
  }
  foo(1, 2, 3);
  ```

4. Prevents you from using duplicate names for properties of objects
  ```javascript
  function foo() {
      "use strict";
      var obj = {
          a: 1,
          a: 2
      };
      console.log(obj); // SyntaxError: Duplicate data property in object literal not allowed in strict mode
  }
  foo();
  ```

5. Prevents you from deleting variables, functions, or arguments
  ```javascript 
  function foo() {
      "use strict";
      var x = 10;
      delete x; // SyntaxError: Delete of an unqualified identifier in strict mode.
  }
  ```
6. Catch typing mistakes in variable names
  ```javascript
  "use strict";
  let helloMyDear;
  helloMyFear = "Hello, my dear!"; // ReferenceError: helloMyFear is not defined
  ```

7. Prevents you from using octal numeric literals
  ```javascript
  function foo() {
      "use strict";
      var x = 010; // SyntaxError: Octal literals are not allowed in strict mode.
  }
  foo();
  ```

8. Prevents you from using `with` statement
  ```javascript
  function foo() {
      "use strict";
      var obj = {
          a: 1,
          b: 2,
          c: 3
      };
      with(obj) { // SyntaxError: Strict mode code may not include a with statement
          console.log(a, b, c);
      }
  }
  foo();
  ```

9. Prevents you from using `eval` function
  ```javascript
    "use strict";
    var x = 10;
    eval("var x = 20;"); 
    console.log(x); // 10

    // Without strict mode
    var y = 10;
    eval("var y = 20;"); 
    console.log(y); // 20
  ```

In strict mode, the scope of variables and functions defined inside an `eval` function is limited to the scope of that `eval` function. In non-strict mode, the scope of variables and functions defined inside an `eval` function is the current scope.






