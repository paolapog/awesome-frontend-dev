`const` and `Object.freeze` in JavaScript are used for making variables and objects __unchangeable__, but they work in different ways.

## const

`const` is used to create a read-only reference to a value. It doesn't mean the value it holds is immutable, just that the variable identifier cannot be reassigned.

Example:

```javascript
const obj = { name: 'John' };
obj.name = 'Doe'; // OK
console.log(obj.name); // Outputs: 'Doe'

obj = { name: 'Smith' }; // TypeError: Assignment to constant variable.
```

**Pros**:

- Prevents reassignment of the variable.
- Makes code easier to reason about when you know a variable can't be reassigned.

**Cons**:

- Doesn't make the value itself immutable.

## Object.freeze

`Object.freeze` makes an object immutable, meaning you can't change its existing properties or add new ones.

Example:

```javascript
const obj = { name: 'John' };
Object.freeze(obj);

obj.name = 'Doe'; // NOT OK
console.log(obj.name); // Outputs: 'John'

obj.age = 30; // NOT OK
console.log(obj.age); // Outputs: undefined
```

**Pros**:

- Makes the object itself immutable.
- Useful when you want to ensure the state of an object doesn't change.

**Cons**:

- Only makes the object shallowly immutable. If the object contains other objects, those can still be modified.
- Can have performance implications if used excessively.

In summary, `const` prevents reassignment of the variable, while `Object.freeze` prevents modification of the object. They can be used together if you want a variable that can't be reassigned and holds an object that can't be modified.