A JavaScript engine is a program or interpreter which executes JavaScript code. A JavaScript engine can be implemented as a standard interpreter, or just-in-time compiler that compiles JavaScript to bytecode in some form.

Here's a simplified overview of how a JavaScript engine works:

1. **Parsing**: The engine reads ("parses") the JavaScript code and turns it into a data structure known as an Abstract Syntax Tree (AST). This represents the syntactic structure of the code.

```javascript
function add(a, b) {
    return a + b;
}

{
    "type": "FunctionDeclaration",
    "id": {
        "type": "Identifier",
        "name": "add"
    },
    "params": [
        {
            "type": "Identifier",
            "name": "a"
        },
        {
            "type": "Identifier",
            "name": "b"
        }
    ],
    "body": {
        "type": "BlockStatement",
        "body": [
            {
                "type": "ReturnStatement",
                "argument": {
                    "type": "BinaryExpression",
                    "operator": "+",
                    "left": {
                        "type": "Identifier",
                        "name": "a"
                    },
                    "right": {
                        "type": "Identifier",
                        "name": "b"
                    }
                }
            }
        ]
    }
}
```

2. **Compilation**: The AST is then compiled into bytecode or machine code. Some engines, like V8, use a technique called Just-In-Time (JIT) compilation, which compiles the code just before it's executed.

3. **Execution**: The machine code is executed. This is the step where the function `add` would actually be performed and produce a result.

4. **Optimization**: While the code is running, the engine collects information that it uses to optimize the code, making it run faster. For example, if it notices that a function is called frequently, it might optimize that function to make it run faster.

5. **Deoptimization**: If the engine's assumptions based on the collected information turn out to be incorrect, the engine can "deoptimize" the code, reverting it back to a less optimized form.

Different JavaScript engines may implement these steps in slightly different ways, but the basic process is the same.

## What is the difference between a JavaScript engine and a JavaScript runtime?
A JavaScript engine and a JavaScript runtime are two different components that work together to execute JavaScript code, but they have distinct roles:

1. **JavaScript Engine**: The JavaScript engine is responsible for parsing JavaScript code into an Abstract Syntax Tree (AST), then converting (or compiling) it into bytecode or machine code, and finally executing it. The engine handles all the low-level operations of interpreting the JavaScript code. Examples include V8 (used in Chrome and Node.js), SpiderMonkey (used in Firefox), and JavaScriptCore (used in Safari).

2. **JavaScript Runtime**: The runtime includes the engine but also provides built-in objects and APIs that provide functionality beyond what is available in the JavaScript language itself. These can include APIs for working with the file system, network, timers, and more. The runtime is the environment in which the JavaScript code runs and interacts. For example, in a browser environment, the runtime includes APIs for manipulating the DOM, handling HTTP requests, and more. In Node.js, the runtime includes APIs for file system access, network operations, etc.

In summary, the JavaScript engine is the core component that parses, compiles, and executes JavaScript code, while the runtime is the environment that provides additional APIs and objects for the JavaScript code to interact with.

## Performance optimization made by JavaScript engine

1. **Just-In-Time (JIT) Compilation**: Instead of interpreting JavaScript or compiling the entire code to bytecode before execution, JIT compilers compile the code at runtime, just before it's executed. This allows the engine to optimize frequently executed code.

2. **Inline Caching**: This is a method to speed up property access in dynamic languages like JavaScript. When a property is accessed, the engine stores the location of the property. The next time the property is accessed, the engine first checks the cache, which can be much faster than a full property lookup.

3. **Hidden Classes**: JavaScript is a prototype-based language, which means objects can change at runtime. However, this can make property access slow. To speed this up, JavaScript engines use hidden classes. When an object is created, the engine creates a hidden class. When a property is added, the engine creates a new hidden class with this property and transitions the object to the new class. This allows the engine to use the same hidden class for objects with the same properties, which can speed up property access.

4. **Garbage Collection**: JavaScript engines automatically manage memory using a process called garbage collection. The engine keeps track of which objects are still in use and which are not. Objects that are no longer in use are considered garbage and their memory is freed. This process is optimized to minimize the impact on performance.

5. **Code Profiling**: JavaScript engines monitor the execution of the code to identify hot paths - parts of the code that are executed frequently. These hot paths are then optimized further.

6. **Deoptimization (Bailout)**: Sometimes, the engine's assumptions about the code turn out to be incorrect. In these cases, the engine "bails out" and deoptimizes the code, reverting it back to a less optimized form that is more general and can handle all cases.

These optimizations are done automatically by the JavaScript engine. As a developer, you don't need to worry about them in most cases.