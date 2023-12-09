The Override keyword is used by a method in a **subclass to override a method in a superclass**.<br/>

```typescript 
class Vehicle {
    startEngine() {
        console.log("Engine started");
    }
}

class Car extends Vehicle {
    override startEngine() {
        console.log("Car engine started with a roar!");
    }
}

const myCar = new Car();
myCar.startEngine();
```