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