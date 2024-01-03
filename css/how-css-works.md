The process of how CSS works under the hood of a browser can be broken down into the following steps:

**1. Loading:**

The first step is loading the CSS. This can happen in a few ways:

- An external CSS file linked via a `<link>` tag in the HTML.
- Inline styles included within a `<style>` tag in the HTML.
- Inline styles applied directly to HTML elements via the `style` attribute.

**2. Parsing:**

Once the CSS is loaded, the browser parses the CSS into a format it can understand. During this process, the browser converts the CSS into a Cascading Style Sheet Object Model (CSSOM), which is a tree-like structure similar to the DOM (Document Object Model) for HTML.

The CSSOM and DOM are combined into a render tree, which is a representation of all the objects to be rendered.

**3. Resolving Conflicts (Cascading and Inheritance):**

If there are conflicting CSS rules, the browser resolves these conflicts using the rules of cascading and inheritance.

- **Cascading**: If multiple rules apply to the same element, the one with the highest specificity wins. If the specificity is the same, the last rule defined wins.
- **Inheritance**: Some CSS property values set on parent elements are inherited by their child elements, and some are not. If no value is set on the child and the property is inheritable, the value from the parent is used.

**4. Layout:**

Once the render tree is built, the browser calculates the layout of each visible element. This involves calculating the exact position and size of each element for the viewport.

**5. Painting:**

After the layout is calculated, the browser paints the pixels for each element in the render tree. This involves drawing out text, colors, images, borders, and shadows, essentially every visual part of the elements.

**6. Compositing:**

Finally, the browser performs compositing, where it draws layers in the correct order to ensure that overlapping elements show up correctly. This step is necessary because some elements can overlap due to positioning, negative margins, or because of certain CSS properties like `z-index`.

In conclusion, the process of how CSS works under the hood of a browser involves loading the CSS, parsing it into a CSSOM, resolving conflicts with cascading and inheritance, calculating the layout, painting the pixels, and finally compositing the layers. This process is complex and optimized for performance to ensure that web pages load and render quickly.