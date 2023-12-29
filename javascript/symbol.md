A `Symbol` is __a unique and immutable data type__ introduced in ES6 (ECMAScript 2015). It is often used as an identifier for object properties.

```javascript
let sym1 = Symbol();
let sym2 = Symbol('foo');
let sym3 = Symbol('foo');

console.log(sym2 === sym3); // false, symbols are unique
```

In this example, even though `sym2` and `sym3` are both initialized with the same description 'foo', they are different symbols.

Attempting to create a `Symbol` using the `new` operator, as shown below, will result in a `TypeError`:

```javascript
const sym = new Symbol(); // TypeError
```

This restriction prevents developers from inadvertently creating a Symbol wrapper object instead of a new Symbol value. This behavior might be unexpected, as it's usually possible to create explicit wrapper objects for other primitive data types (like `new Boolean`, `new String`, and `new Number`).

If you absolutely need to create a Symbol wrapper object, you can achieve this using the `Object()` function:

```javascript
const sym = Symbol('foo');

const symObj = Object(sym);

console.log(typeof symObj); // object
```

**Pros:**

1. **Uniqueness**: Every symbol is unique. Even if you create many symbols with the same description, they are different. This uniqueness can be useful when you want to add properties to objects with a guarantee of not overwriting existing properties.

2. **Privacy**: Symbols allow for a form of "private" properties when used as keys on objects, as they are not enumerated over in a `for...in` loop or `Object.keys()` invocation.

**Cons:**

1. **Debugging**: It can be harder to debug objects with symbol keys as they are not easily visible.

2. **Compatibility**: Symbols are not fully supported in older browsers, which can lead to compatibility issues.

Kyle Simpson, in his "You Don't Know JS" series, about Symbols:

> "Symbols are not really a new type of value where you'd need to create and manage them in your program's logic. Instead, think of them mostly as a new kind of property name that's mostly hidden from your program's operation, useful only for their collision-avoidance characteristics."