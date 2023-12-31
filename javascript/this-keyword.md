In JavaScript, `this` is a special keyword that's set when a function is called, and it refers to the context in which the function was called. The value of `this` is not determined by how a function is defined, but by how it's called.

```javascript
let obj = {
  name: 'John',
  greet: function() {
    console.log(`Hello, ${this.name}`);
  }
};

obj.greet(); // "Hello, John"
```

In this example, `this` inside the `greet` method refers to `obj`.

**Pros:**

- It allows you to access the context in which a function was called.
- It's very useful in "object-oriented programming" (in this case we are talking about [prototypal inheritance](./prototypal-inheritance.md), where you want methods to have access to their object's properties.

**Cons:**

- The value of `this` can be confusing, especially in nested functions or callbacks where it might not be what you expect.
- It can lead to bugs if not understood correctly.

Kyle Simpson, in his "You Don't Know JS" series, has a lot to say about `this`:

> "Instead of relying on `this`, you could use an object reference to keep the binding to the desired object, making the `this` style of coding unnecessary. It's a choice of style and readability, not of functionality."

And:

> "I think `this` is cool, but it's also easily one of the most misunderstood mechanisms in JavaScript and is often avoided as such."