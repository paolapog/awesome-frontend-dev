__Native__ objects: These are core objects that are always accessible in JavaScript, regardless of the environment in which the code is running. They are defined in the ECMAScript specification and include objects like `String`, `Math`, `RegExp`, `Object`, `Function`, and others.
```javascript
let str = new String("Hello World"); // Using the String built-in object
console.log(str); // "Hello World"
```
__Host__ objects: These are objects provided by the host environment in which the JavaScript is running. In a browser environment, host objects include `window`, `XmlHttpRequest`, and DOM nodes. However, host objects can vary depending on the environment. For instance, when JavaScript is run in a server-side environment like Node.js, different host objects like global and process are available.
```javascript
console.log(window.location.href); // Using the window host object in a browser environment
console.log(process.version); // Using the process host object in a Node.js environment

```