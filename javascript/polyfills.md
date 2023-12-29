Polyfills are piece of code designed **to extend modern functionality** to older browsers that lack built-in support for those features. 
They serve as a **bridge to fill the gap** between the JavaScript language features and APIs that are available in modern browsers and the limited capabilities of older browser versions. <br />
When a new JavaScript feature or API is introduced, it takes time for all major browsers to adopt and support it. During this transitional period, developers can employ polyfills to ensure their code functions consistently across various browsers.
Polyfills work by identifying whether a specific feature or API is absent and then supplying a custom implementation of that feature using existing JavaScript capabilities.
Polyfills are usually available as a library. They can be included in a web page using a `<script>` tag or loaded dynamically at runtime using a module [bundler](./bundler-vs-transpiler.md) such as Webpack or Rollup.
Polyfills are not a replacement for [transpilers](./bundler-vs-transpiler.md) such as Babel. Transpilers convert code written in one language to another. For example, Babel converts code written in ES6 to ES5 so that it can be executed in older browsers. Polyfills, on the other hand, are used to add support for new features that are not available in older browsers. <br/>
Polyfills are not a new concept. They have been around for a long time and have been used to add support for features such as `Array.prototype.forEach` and `Array.prototype.map` in older browsers. <br />
Example of a polyfill for `Array.prototype.map`:
```js
if (!Array.prototype.map) {
  Array.prototype.map = function(callback, thisArg) {
    var T, A, k;
    if (this == null) {
      throw new TypeError(' this is null or not defined');
    }
    var O = Object(this);
    var len = O.length >>> 0;
    if (typeof callback !== 'function') {
      throw new TypeError(callback + ' is not a function');
    }
    if (arguments.length > 1) {
      T = thisArg;
    }
    A = new Array(len);
    k = 0;
    while (k < len) {
      var kValue, mappedValue;
      if (k in O) {
        kValue = O[k];
        mappedValue = callback.call(T, kValue, k, O);
        A[k] = mappedValue;
      }
      k++;
    }
    return A;
  };
}
```
The above polyfill checks whether the `Array.prototype.map` method is available. If it is not available, it adds a custom implementation of the method to the `Array.prototype` object. <br />

## Shim vs Polyfill
A shim is a piece of code that intercepts API calls and provides a layer of abstraction. It is used to transparently add support for a feature that is not available in the current environment. <br />
A polyfill is a piece of code (is a type of shim, in a certain way) that provides the functionality that is not natively available. It is used to add support for a feature that is not available in the current environment. <br />
Example of a shim for `Date.now`:
```js
if (!Date.now) {
  Date.now = function now() {
    return new Date().getTime();
  };
}
```
The `Date.now` function is a feature introduced in ES5. In ES3, the equivalent syntax would be `new Date().getTime()`. If you utilize the es5-shim, you can employ `Date.now`, and it will execute normally if the browser supports ES5. However, if the browser is operating on the ES3 engine, es5-shim will intercept the Date.now call and return `new Date().getTime()` as a substitute. This process of interception and substitution is referred to as **shimming**.
 <br />