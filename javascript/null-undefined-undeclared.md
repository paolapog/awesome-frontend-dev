In JavaScript, `null`, `undefined`, and undeclared are three states that a variable can be in, each with its own distinct meaning:

1. **undefined**: A variable is `undefined` if it has been declared, but no value has been assigned to it (yet).

```javascript
let myVar;
console.log(myVar); // undefined
```

2. **null**: `null` is a value that represents no value. It is often used to indicate that a variable should have no value. It's different from `undefined` in the sense that it has been explicitly assigned.

```javascript
let myVar = null;
console.log(myVar); // null
```

3. **undeclared**: A variable is undeclared if it has not been declared anywhere in the code. Trying to access an undeclared variable results in a `ReferenceError`.

```javascript
console.log(myVar); // ReferenceError: myVar is not defined
```

It's important to note that `undefined` and `null` are actually values in JavaScript, while undeclared means that the variable has not been created at all. 

Also, JavaScript has `typeof` operator which returns a string indicating the type of the unevaluated operand. `typeof` operator returns `undefined` for variables that have not been assigned a value, and also for variables that have not been declared at all. However, trying to directly access an undeclared variable will still throw a `ReferenceError`.

To verify if a value is `null`, use the strict equality operator (===). Avoid using the abstract equality operator (==) for this purpose, as it will return true for both null and undefined values.


```javascript
let myVar;
console.log(typeof myVar); // "undefined"
console.log(typeof undeclaredVar); // "undefined"
console.log(undeclaredVar); // ReferenceError: undeclaredVar is not defined

let myVar1 = null;
let myVar2 = undefined;
// Using strict equality
console.log(myVar1 === null); // true
console.log(myVar2 === null); // false
// Using abstract equality
console.log(myVar1 == null); // true
console.log(myVar2 == null); // true
```
For best practices, always ensure your variables are neither undeclared nor unassigned. If you don't plan to use them immediately after declaration, explicitly initialize them with `null`.