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
if you remove the keyword ```declare```, it will not compile, instead saying that the name D3 is already defined. This is because in TypeScript, declare var defines a variable that may or may not have already been defined elsewhere. In our case, we know that it exists, but TypeScript doesn’t.

**Use Cases:** 

1. **Third-Party Libraries:** As we said above, If you're using a library (like jQuery, D3, etc.) that doesn't provide TypeScript typings, you can use `declare` to tell TypeScript that these libraries exist and what their types are. This is what's happening in your active file.

```typescript
declare var $: any; // Now TypeScript knows that $ exists
```

2. **Existing JavaScript Variables:** If you're migrating a JavaScript project to TypeScript, there might be some global variables that TypeScript is unaware of. You can use `declare` to tell TypeScript about these.

```typescript
declare var existingVar: any; // Now TypeScript knows that existingVar exists
```

3. **TypeScript Type Definitions (`*.d.ts` files):** These are used to provide TypeScript types for JavaScript libraries. They often use `declare` to define the shape of the library's API.

```typescript
declare namespace MyLibrary {
  function doSomething(input: string): number;
}
```

`declare` is used for writing "type" code that doesn't produce any "real" JavaScript code. It's just for TypeScript's static type checking.