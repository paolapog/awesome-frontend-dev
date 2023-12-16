In TypeScript, a string literal type is a type that represents a **specific set of string values**. This is similar to how enum types work, except that string literal types have no computed members.
```typescript
type Easing = "ease-in" | "ease-out" | "ease-in-out";
class UIElement {
  animate(dx: number, dy: number, easing: Easing) {
    if (easing === "ease-in") {
      // ...
    } else if (easing === "ease-out") {
    } else if (easing === "ease-in-out") {
    } else {
      // It's possible that someone could reach this
      // by ignoring your types though.
    }
  }
}
let button = new UIElement();
button.animate(0, 0, "ease-in");
button.animate(0, 0, "uneasy"); // error: "uneasy" is not allowed here
```
Template literal types **build** on string literal types, and have the ability to expand into many strings via unions.<br />
They have the same syntax as [template literal strings in JavaScript](../javascript/template-literal-strings.md), but are used in type positions. When used with concrete literal types, a template literal produces a new string literal type by concatenating the contents. <br/>
Some __use cases__: <br/>
- **String interpolation** via tagged template literals
example: 
```typescript
type Color = "red" | "blue";
type Quantity = "one" | "two";
type Fish = `${Quantity | Color} fish`;
let fish: Fish = "one fish"; // OK
fish = "two fish"; // OK
fish = "red fish"; // OK
```
- **Type transformation** via mapped types
example: 
```typescript
type Getters<Type> = {
  [Property in keyof Type as `get${Capitalize<string & Property>}`]:
    () => Type[Property]
};
interface Person {
  name: string;
  age: number;
  location: string;
}
type FunnyPerson = Getters<Person>;
// same as
type FunnyPerson = {
    getName: () => string;
    getAge: () => number;
    getLocation: () => string;
}
```
- **Type transformation** via key remapping in mapped types
example: 
```typescript
type RemoveTypeField<Type> = {
  [Property in keyof Type as Exclude<Property, "type">]: Type[Property]
};
interface Circle {
  type: "circle";
  radius: number;
}
type TypelessCircle = RemoveTypeField<Circle>;
// same as
type TypelessCircle = {
    radius: number;
}
```
- **Type transformation** via recursive mapped types
example: 
```typescript
type Getters<Type> = {
  [Property in keyof Type as `get${Capitalize<string & Property>}`]:
    Type[Property] extends Function ? Property : never
};
interface Person {
  name: string;
  age: number;
  location: string;
  getFavouriteFood: () => string;
}
type FunctionPropertyNames<T> = {
  [K in keyof T]: T[K] extends Function ? K : never;
}[keyof T];
type Getters<Type> = {
  [Property in FunctionPropertyNames<Type> as `get${Capitalize<string & Property>}`]:
    Type[Property]
};
type FunnyPerson = Getters<Person>;
// same as
type FunnyPerson = {
    getName: () => string;
    getAge: () => number;
    getLocation: () => string;
    getFavouriteFood: () => string;
}
```