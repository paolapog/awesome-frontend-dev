Dynamic **import** expressions are a new feature and part of ECMAScript that allows users to **asynchronously request a module** at any arbitrary point in your program.<br/>

This means that you can conditionally and lazily import other modules and libraries. For example, here’s an async function that only imports a utility library when it’s needed:<br />

```javascript
async function getZipFile(name, files) {
  const zipUtil = await import("./utils/create-zip-file");
  const zipContents = await zipUtil.getContentAsBlob(files);
  return new File(zipContents, name);
}
```
