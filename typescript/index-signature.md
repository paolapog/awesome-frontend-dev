Index signature is used to represent the type of **object/dictionary** when the values of the object are of consistent types.<br/>
Index signature is also known as **keyed collection**. <br/>

```typescript
// Syntax
{ [key: typeForKeys]: typeForValues }

interface Dictionary {
    [index: string]: string;
}

let phoneBook: Dictionary;

phoneBook = {
    "Alice": "123-456-7890",
    "Bob": "987-654-3210",
    "Charlie": "456-789-0123"
};

let aliceNumber: string = phoneBook["Alice"]; // "123-456-7890"
```

These values will be consistent with the type string. This makes a perfect opportunity for us to apply the index signature.<br/>
__What if we try to add a value of a different type other than the type defined in the index signature?__

```typescript
interface StringDictionary {
    [index: string]: string;
}

let myDict: StringDictionary;

myDict = {
    "name": "Alice",
    "age": "25"
};

// This will cause an error because the value is not a string
myDict["height"] = 170; // Error: Type 'number' is not assignable 
```

but if we create a union type with number and string, it will work.

```typescript
interface StringDictionary {
    [index: string]: string | number;
}

let myDict: StringDictionary;

myDict = {
    "name": "Alice",
    "age": "25"
};

myDict["height"] = 170; 
```
**Remember**: Index signature parameter type must be ```string```, ```number```, ```symbol```, or a template literal type, otherwise TypeScript will give an error.<br/>