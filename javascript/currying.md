Currying in JavaScript is a functional programming technique that involves **converting a function with multiple arguments into a series of nested functions**. This leads to the generation of a new function that expects each following argument one after the other. <br />

In simpler terms, rather than a function receiving all its arguments simultaneously, it initially takes the first one and produces a new function. This new function, in turn, takes the second argument and yields another function, continuing this pattern until all arguments are satisfied. <br />

Curried functions are formed by **creating a sequence of closures**, wherein each closure defines and immediately returns its inner function. <br />

```javascript
// normal function with arity of 3
function sum(a, b, c) {
    return a + b + c;
}
sum(1,2,3); // 6


// curried function
function sum(a) {
    return (b) => {
        return (c) => {
            return a + b + c
        }
    }
}
console.log(sum(1)(2)(3)) // 6

```

**Pros**:
- It can make your code more readable and expressive.
- It allows you to create specialized functions from more general ones.
- It can be useful in asynchronous code because it allows you to delay a computation until all the arguments are available.

**Cons**:
- It can make your code harder to understand if you're not familiar with the concept.
- It can lead to a performance overhead because of the creation of many intermediate functions.

Kyle Simpson, author of the "You Don't Know JS" book series, says: 
"Currying is a way of thinking about functions that allows us to use the functional nature of JavaScript to our advantage."