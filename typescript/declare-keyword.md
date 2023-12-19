To describe the **shape of libraries** not written in TypeScript, we need to declare the API that the library exposes. Because most JavaScript libraries expose only a few top-level objects, namespaces are a good way to represent them.
  
```typescript
declare namespace D3 {
    export interface Selectors {
        select: {
            (selector: string): Selection;
            (element: EventTarget): Selection;
        };
    }

    export interface Event {
        x: number;
        y: number;
    }

    export interface Base extends Selectors {
        event: Event;
    }
}
```

We have already the D3 library installed in our project but we don't have the type definition file for it, so TypeScript will give us an error if we try to use it. To fix this we need to create a file called ```d3.d.ts``` in the root of our project and add the above code to it. Now we can use the D3 library without any errors. <br/>
if you remove the keyword ```declare```, it will not compile, instead saying that the name D3 is already defined. This is because in TypeScript, declare var defines a variable that may or may not have already been defined elsewhere. In our case, we know that it exists, but TypeScript doesn’t.<br/>
