In HTML, the `<script>` tag is used to embed or reference JavaScript code within a document. The `async` and `defer` attributes change the way the script is loaded and executed. Here's how they differ:

1. **`<script>`**: By default, scripts are loaded and executed immediately as soon as they're encountered in the HTML. This means that the parsing of the HTML is blocked until the script is loaded and executed.

   Pros:
   - It ensures that the script is loaded and executed before the browser continues parsing the rest of the HTML.

   Cons:
   - It can lead to a poor user experience because it blocks the rendering of the page.

   Use Case: Use this when your script is small and needs to modify the DOM before it's fully parsed.

2. **`<script async>`**: The `async` attribute means that the script is loaded in the background, and it will be executed as soon as it's loaded, even if the HTML is still being parsed.

   Pros:
   - It doesn't block the parsing of the HTML.

   Cons:
   - It doesn't guarantee the order of execution. Scripts may execute in a different order than they appear in the HTML.

   Use Case: Use this when your script is independent and doesn't rely on other scripts or on the DOM being fully parsed.

3. **`<script defer>`**: The `defer` attribute means that the script is loaded in the background, but it's not executed until the HTML is fully parsed.

   Pros:
   - It doesn't block the parsing of the HTML.
   - It guarantees the order of execution. Scripts will execute in the order they appear in the HTML.

   Cons:
   - It delays the execution of the script until the HTML is fully parsed.

   Use Case: Use this when your script relies on the DOM being fully parsed and/or on other scripts that also use `defer`.

In summary, `async` and `defer` can improve the performance of your web page by allowing scripts to be loaded in the background. However, they should be used judiciously, taking into account the dependencies and requirements of your scripts.