In TypeScript, getters and setters are special methods that provide read and write access to an object's properties. They are a part of the ES5 standard and are fully supported in TypeScript.

**Getters** are methods that get the value of a specific property. **Setters** are methods that set the value of a specific property.

```typescript
class MyClass {
  private _myProp: string;

  get myProp(): string {
    return this._myProp;
  }

  set myProp(value: string) {
    if (!value) {
      throw new Error('Invalid value!');
    }
    this._myProp = value;
  }
}

let instance = new MyClass();
instance.myProp = 'Hello, world'; // OK
console.log(instance.myProp); // "Hello, world"
```

In this example, `myProp` is a property with a getter and a setter. The getter returns the value of `_myProp`, and the setter validates the new value before setting `_myProp`.

**Use Cases:**

1. **Validation:** You can use setters to validate the data before setting a property. This ensures that your object is always in a valid state.

2. **Encapsulation:** Getters and setters provide a way to encapsulate the internal representation of an object's data. This allows you to change how the data is stored internally without affecting code that uses the object.

3. **Computed Properties:** You can use getters to create computed properties that are calculated based on other properties.

```typescript
class Rectangle {
  constructor(public width: number, public height: number) { }

  get area(): number {
    return this.width * this.height;
  }
}

let rect = new Rectangle(5, 10);
console.log(rect.area); // 50
```

In this example, `area` is a computed property that calculates the area of the rectangle based on its width and height.