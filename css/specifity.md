CSS specificity is a set of rules applied by browsers to determine which CSS rule will be applied to an element. The specificity is calculated based on the different kinds of selectors in a CSS rule.

Here's how specificity is calculated:

1. **Inline styles**: An inline style is attached directly to the element to be styled. Example: `<h1 style="color: #ffffff;">`. Inline styles have the highest specificity.

2. **IDs**: An ID is a unique identifier for the page elements, such as `#navbar`.

3. **Classes, attributes, and pseudo-classes**: This category includes `.classes`, `[attributes]`, and `:pseudo-classes`.

4. **Elements and pseudo-elements**: This includes `element` and `::pseudo-elements`.

Each type of selector carries a different "weight". A style declaration's specificity is calculated as follows:

- Count the number of ID selectors in the selector (= a).
- Count the number of class selectors, attributes selectors, and pseudo-classes in the selector (= b).
- Count the number of type selectors and pseudo-elements in the selector (= c).
- Ignore the universal selector.

Specificity is usually represented as a three-digit number: `a-b-c`. 

**Examples:**

```css
/* specificity = 0-0-1 */
h1 {
  color: red;
}

/* specificity = 0-1-0 */
.special {
  color: green;
}

/* specificity = 0-1-1 */
.special h1 {
  color: blue;
}

/* specificity = 1-0-0 */
#top {
  color: yellow;
}
```

In the above examples, if an `h1` tag had all these classes, the color would be yellow because the ID selector (`#top`) has the highest specificity.

**Important points:**

- If two selectors apply to the same element, the one with higher specificity wins.
- If two selectors have the same specificity, the last one defined wins.
- `!important` overrides any other declarations, but should be used sparingly as it breaks the natural cascading in your stylesheets.

**Specificity Hierarchy:**

1. `!important`: This has the highest specificity.
2. Inline styles: An inline style is attached directly to the element to be styled.
3. IDs: Selectors that contain an ID.
4. Classes, attributes, and pseudo-classes: Selectors that contain a class.
5. Elements and pseudo-elements: Selectors that contain a tag or pseudo-element.

Remember, when multiple rules have equal specificity, the last rule declared in the CSS will be the one that is applied.

## Override CSS specificity and why you shouldn't

There are a few ways to override CSS specificity:

1. **Using `!important`**: This is the most powerful tool in CSS for increasing specificity. When you add `!important` to a style, it will override any other declarations. However, using `!important` is often considered bad practice because it makes debugging more difficult by breaking the natural cascades in your stylesheets and can lead to code that is harder to maintain.

```css
p {
  color: blue !important; /* This will override any other color property on p elements */
}
```

2. **Increasing the specificity**: You can increase the specificity of your selector by adding a class, id, or even another element to the selector.

```css
body p {
  color: blue; /* This has higher specificity than just 'p' */
}
```

3. **Using a more specific selector**: ID selectors have higher specificity than attribute selectors, classes, and pseudo-classes. Attribute selectors, classes, and pseudo-classes have higher specificity than element types. So using a more specific selector can override styles with lower specificity.

```css
#myId {
  color: blue; /* This will override color property of any other selector that targets the same element but has lower specificity */
}
```

4. **Using the same specificity, but later source order**: If two selectors have the same specificity, the one that comes last in the CSS will be used.

```css
p {
  color: red;
}

p {
  color: blue; /* This will be applied because it comes later */
}
```

5. **Inline styles**: Inline styles applied to an element within the HTML will always override any styles in external stylesheets, and will even override similar styles written in the same element with `!important`.

```html
<p style="color: blue;">This will always be blue.</p>
```

And these are the reasons why you shouldn't:

1. **Maintainability**: Overriding specificity often leads to more complex code, making it harder to understand and maintain. It can create a situation where you're constantly increasing specificity to override previous styles, leading to a specificity war. This can make the CSS codebase large and unwieldy.

2. **Predictability**: Overriding specificity can lead to styles behaving in ways that are hard to predict. This is especially true when `!important` is used, as it breaks the natural cascading flow of stylesheets.

3. **Performance**: Overly specific CSS can lead to performance issues. Browsers read CSS from right to left, and if a browser has to match a long, specific selector, it can slow down the rendering of the page.

4. **Reusability**: Highly specific CSS is less reusable. If you have a style defined with high specificity, you can't easily apply that style to other elements or in different contexts.

5. **Debugging**: It can be difficult to debug issues related to CSS specificity. If a style isn't being applied as expected, it can be hard to figure out why if there are lots of rules with high specificity that could be affecting it.

Instead of overriding specificity, it's often better to work with it. Use methodologies like BEM, OOCSS, or SMACSS to write CSS that is easy to understand, maintain, and debug. These methodologies encourage styles that are low-specificity and therefore more reusable and less likely to result in unexpected behavior.

## BEM Methodology

BEM stands for Block, Element, Modifier. It's a methodology for creating reusable, maintainable, and scalable code. It's especially useful in CSS to help developers understand the relationship between HTML and CSS in a given project.

BEM is based on three principles:

1. **Block**: A block is a standalone entity that is meaningful on its own. Blocks can be simple or complex and can contain other blocks or elements. For example, a header, container, menu, or footer.

2. **Element**: An element is a part of a block that has no standalone meaning and is semantically tied to its block. For example, a menu item, list item, or a header title.

3. **Modifier**: A modifier is a flag on a block or element used to change appearance or behavior. For example, a button block might have a 'disabled' modifier to style the button differently when it's not active.

In terms of CSS class naming convention, BEM follows this pattern:

- Block: `.block`
- Element: `.block__element`
- Modifier: `.block--modifier` or `.block__element--modifier`

**Example:**

```html
<div class="menu">
  <button class="menu__item menu__item--disabled">Option 1</button>
  <button class="menu__item">Option 2</button>
</div>
```

In this example, `menu` is the block, `menu__item` is an element, and `menu__item--disabled` is a modifier.

**Benefits of BEM:**

- **Modularity**: BEM methodology allows for the creation of independent blocks and elements that can be reused and moved around in your layout.

- **Scalability**: BEM is great for large projects where the code must be scalable and maintainable.

- **Code clarity and readability**: The naming convention in BEM makes the code easier to read and understand. It's clear to see the relationships between different parts of the code.

- **No specificity wars**: Because each class is unique, there's no need for specificity hacks. This makes the code cleaner and easier to maintain.