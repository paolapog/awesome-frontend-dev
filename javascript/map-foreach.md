`map` and `forEach` are both array methods in JavaScript that iterate over an array.

## Array.prototype.map()

`map` creates a new array by calling a provided function on every element in the calling array.

```javascript
let numbers = [1, 2, 3, 4, 5];
let squares = numbers.map(num => num * num);
console.log(squares); // [1, 4, 9, 16, 25]
```

**Pros**:
- It returns a new array, leaving the original array unchanged, which is in line with functional programming principles.
- It always returns a new array of the same length as the input array.

**Cons**:
- It's not efficient if you're not using the returned array, because it always returns a new array.

## Array.prototype.forEach()

`forEach` executes a provided function once for each array element. It does not return anything.

```javascript
let numbers = [1, 2, 3, 4, 5];
numbers.forEach((num, index) => {
    console.log(`Number ${num} is at index ${index}`);
});
```

**Pros**:
- It's useful for applying a function to every element in an array for side effects (like logging or updating the DOM).
- It doesn't return a new array, so it's more efficient than `map` if you don't need a new array.

**Cons**:
- It doesn't return anything, so you can't chain other array methods after it.
- It alters the original array (if you change elements), which is not in line with functional programming principles.

In summary, use `map` when you want to transform elements in an array and use the result. Use `forEach` when you want to apply a function to each element in an array for side effects.