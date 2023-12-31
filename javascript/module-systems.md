JavaScript has several module systems that have been used over the years: AMD (Asynchronous Module Definition), CommonJS, and ES modules (ESM) .

**AMD (Asynchronous Module Definition)**

AMD is a JavaScript API for defining modules where both the module and dependencies can be asynchronously loaded. It's well suited for the browser environment where synchronous loading of modules incurs performance, usability, debugging, and cross-domain access issues.

Example:

```javascript
define(['dependency1', 'dependency2'], function(dependency1, dependency2) {
  // Module code here
});
```

**Pros**:

- Asynchronous by nature.
- Suitable for use in the browser.

**Cons**:

- Syntax is a bit more complex and harder to read.
- Less popular and less widely adopted than CommonJS and ES6 modules.

**CommonJS**

CommonJS is a module format that was primarily designed for server-side JavaScript and became popular through Node.js. It's a simple and straightforward module system where you export an object which becomes the module, and require other modules by their filenames.

Example:

```javascript
const dependency1 = require('dependency1');
const dependency2 = require('dependency2');

// Module code here

module.exports = {
  // Exported module interface
};
```

**Pros**:

- Simple and straightforward syntax.
- Synchronous by nature, which is simpler to understand and use.
- Widely adopted in Node.js.

**Cons**:

- Not designed with the browser in mind. Synchronous loading can be a performance issue in the browser.
- Not as flexible as ES modules.

**ES Modules**

ES modules are the official standard format to package JavaScript code for reuse. Modules are defined using a variety of `import` and `export` statements.

Example:

```javascript
import dependency1 from 'dependency1';
import { namedExport } from 'dependency2';

// Module code here

export default {
  // Exported module interface
};
```

**Pros**:

- Official standard with support in all modern browsers and Node.js.
- Static structure allows for compile-time checks and advanced features like tree shaking.
- More flexible syntax with support for named and default exports.

**Cons**:

- More complex syntax compared to CommonJS.
- Dynamic loading requires using the `import()` function which returns a [Promise](./async-await-promises.md) .
- Older browsers and versions of Node.js may require a transpiler like Babel.