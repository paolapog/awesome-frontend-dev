The `display` property in CSS determines how an element is displayed in the [document flow](./document-flow.md). The three most basic values are `block`, `inline`, and `inline-block`.

1. **Block**: Block-level elements start on a new line and stretch out to the left and right as far as they can. Examples of block-level elements include `<div>`, `<p>`, and `<h1>` to `<h6>`. 

   Example:
   ```html
   <div style="display: block; background-color: lightblue;">I'm a block-level element.</div>
   ```
   Use Case: Use block elements when you want to structure your page with sections or groupings of content. They are also useful when you want an element to take up the full width of its parent.

2. **Inline**: Inline elements do not start on a new line and only take up as much width as necessary. This means you cannot set `width` and `height` properties for inline elements. Examples of inline elements include `<span>`, `<a>`, and `<img>`.

   Example:
   ```html
   <span style="display: inline; background-color: lightyellow;">I'm an inline element.</span>
   ```
   Use Case: Use inline elements when you want to style a part of a text. For example, to highlight a word in a sentence, you would wrap the word in a `<span>` with a class that changes the color.

3. **Inline-Block**: Inline-block elements are a hybrid of the two. They can appear next to each other like inline elements, but you can set their `width` and `height` like block elements.

   Example:
   ```html
   <div style="display: inline-block; width: 200px; height: 100px; background-color: lightgreen;">I'm an inline-block element.</div>
   ```
   Use Case: Use inline-block when you want to place elements side-by-side (like inline), but also want to specify their dimensions or want them to have block-like properties. They're useful for things like navigation menus and buttons.

Remember, the `display` property can be overridden with CSS, so you can make a block element display as inline, or vice versa. Understanding these display properties is crucial for controlling layout and alignment in CSS.