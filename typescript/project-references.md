Project references are a feature in TypeScript that __allows one TypeScript project to depend on another__. They were introduced to make it easier to split your code into smaller projects, since managing large codebases can be challenging.

**Pros**:

**1. Improved Build Times:**

By splitting your code into smaller projects, TypeScript only needs to rebuild the parts of the codebase that have changed. This can significantly improve build times for large codebases.

**2. Better Code Organization:**

Project references can help you structure your codebase in a more logical and manageable way. Each project can focus on one aspect of your application, making the code easier to understand and maintain.

**3. Easier Code Sharing:**

If you have code that needs to be shared between multiple projects, you can put it in a separate project and have the other projects reference it. This is much easier than copying the code between projects.

**4. Enhanced Tooling:**

When using project references, editors and other tools can provide better navigation and autocompletion. They can understand the dependencies between projects and provide more accurate suggestions.

Here's an example of how to use project references. Suppose you have two projects, `core` and `app`, where `app` depends on `core`. You would specify this in the `tsconfig.json` file of the `app` project like this:

```json
{
  "compilerOptions": {
    // ...
  },
  "references": [
    { "path": "../core" }
  ]
}
```

The `app` project references the `core` project. When you build the `app` project, TypeScript will first build the `core` project.

**Cons**:

**1. Circular Dependencies:**

Avoid creating circular dependencies between projects. This can lead to unexpected behavior and can make your code harder to understand and maintain.

**2. Incorrect Paths:**

Ensure that the paths in the "references" array in your `tsconfig.json` file are correct. Incorrect paths can lead to build errors or unexpected behavior.

**3. Inconsistent TypeScript Versions:**

If you're using different versions of TypeScript in different projects, you might encounter inconsistencies or errors. It's best to use the same TypeScript version across all projects.

**4. Ignoring the `outDir` Setting:**

If you're compiling your TypeScript files to JavaScript, make sure to set the `outDir` option in your `tsconfig.json` file. This tells TypeScript where to output the compiled JavaScript files. If you don't set this, the compiled files could end up in unexpected places.

**5. Not Using `composite` Option:**

For a project to be used as a reference, it needs to have the `composite` option set to `true` in its `tsconfig.json` file. If you forget to do this, you won't be able to use the project as a reference.

**6. Not Building Referenced Projects:**

When you build a project that has references to other projects, TypeScript will build the referenced projects first. If you're not aware of this, it can lead to confusion. Make sure to build your projects in the correct order.