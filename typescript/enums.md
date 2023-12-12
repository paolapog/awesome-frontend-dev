Enums allow a developer to define a set of named constants. Using enums can make it easier to document intent, or create a set of distinct cases. TypeScript provides both numeric and string-based enums. <br />

```typescript
enum Direction {
  Up,
  Down,
  Left,
  Right,
}
```
above code compiles to:
```javascript
var Direction;
(function (Direction) {
    Direction[Direction["Up"] = 1] = "Up";
    Direction[Direction["Down"] = 2] = "Down";
    Direction[Direction["Left"] = 3] = "Left";
    Direction[Direction["Right"] = 4] = "Right";
})(Direction || (Direction = {}));
```
Functioning both as a mapping from strings to numbers (e.g., accessed through Direction.Up or Direction['Up']) and as a mapping from numbers to strings, this bidirectional mapping proves valuable for debugging or logging scenarios. In such situations, having the ability to convert values like 0 or 1 to their corresponding strings, such as "Up" or "Down," is particularly useful. <br />
String enums are a similar concept, but have some subtle runtime differences. In a string enum, each member has to be constant-initialized with a string literal, or with another string enum member.
```typescript
enum Direction {
  Up = "UP",
  Down = "DOWN",
  Left = "LEFT",
  Right = "RIGHT",
}
```
You can have also a mixed enum with string and numeric members, but it's not advised to do so. <br />
It is possible to ```declare``` entities that the compiler should be aware of without generating actual code. This proves beneficial when dealing with libraries like jQuery, where you desire type information about an object (e.g., $) but do not require the compiler to produce any code. Declarations made in this way are considered to be in an "ambient" context, as outlined in the specification and other documentation. It's essential to recognize that all declarations in a ```.d.ts``` file are inherently "ambient," with the presence or absence of an explicit declare modifier depending on the type of declaration. <br/>
For reasons related to performance and code size, it is commonly more efficient to replace a reference to an enum member with its numeric equivalent during the compilation process. This process is called **inlining** (substitution), and it is performed when the compiler can guarantee that the enum member is a constant (so it doesn't change in time). <br/>

```typescript
enum Colors {
  Red = 1,
  Green = 2,
  Blue = 3
}

const selectedColor = Colors.Green;
// TypeScript might emit: "const selectedColor = 2;" during compilation
```

Enum members can **either be computed or not**. <br/>
A computed enum member is one whose value is not known at compile-time. References to computed members cannot be inlined, of course. Conversely, a non-computed enum member is once whose value is known at compile-time. References to non-computed members are always inlined.
Which enum members are computed and which are non-computed? First, all members of a const enum are constant (i.e. non-computed), as the name implies. For a non-const enum, it depends on whether you're looking at an ambient (declare) enum or a non-ambient enum.

A member of a declare enum (i.e. ambient enum) is constant if and only if it has an initializer. Otherwise, it is computed. Note that in a declare enum, only numeric initializers are allowed.

```typescript
declare enum Example {
  A = 1,
  B, // Error! 'B' is not constant-initialized, so it is considered computed
}
```
An enum declaration can have the **const modifier**. If an enum is const, **all references to its members inlined**.
```typescript
const enum Colors {
  Red = 1,
  Green = 2,
  Blue = 3
}

const selectedColor = Colors.Green;
// TypeScript will always emit: "const selectedColor = 2;" 
```
The const modifier is useful in situations where enum values are inlined, and you don't want to pay the cost of generating the enum object at runtime. <br/>
If an enum declaration does not have the const modifier, references to its members are inlined only if the member is non-computed. <br/>

A __declare enum__ will not emit an object. References to its members are inlined if those members are computed. <br/>
A __declare const enum__ is not different from a const enum, except in the case of ```--preserveConstEnums```, __non-declare const__ enums will emit an object. Inlining is not affected. This is useful for debugging.