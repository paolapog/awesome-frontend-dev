CSS inheritance is a key feature of CSS that influences how styles are applied to elements. It controls how properties are transferred from parent elements to their children.

**How it works:**

When you apply a style to an element, that style can potentially affect the element's child elements. Whether or not it does depends on the property. Some CSS properties are inherited by default, while others are not.

For example, if you set the `color` property on a `<div>`, that color will apply to any text inside the `<div>`, unless you've set a different color on the text itself. This is because the `color` property is inheritable.

```css
div {
  color: blue;
}
```

In this case, any text inside this `<div>` will be blue, unless a different color is specified on the text element.

On the other hand, if you set the `background-color` property on a `<div>`, that background color will not apply to any child elements. This is because the `background-color` property is not inheritable.

```css
div {
  background-color: yellow;
}
```

In this case, the background color will not apply to child elements unless explicitly set on them.

**Use Cases:**

In CSS, many properties are inheritable, meaning their values are automatically passed from parent elements to their children. However, not all properties are inheritable. Here are some commonly used inheritable properties:

- `color`
- `font-family`
- `font-size`
- `font-weight`
- `line-height`
- `text-align`
- `text-indent`
- `text-transform`
- `letter-spacing`
- `word-spacing`
- `white-space`
- `direction`
- `visibility`

This is not an exhaustive list, and the inheritability of a property is defined in its specification. If a property is not inheritable by default, you can still force it to be inherited by using the `inherit` keyword as its value.

For example, `background-color` is not an inheritable property. But you can force it to be inherited like this:

```css
div {
  background-color: inherit;
}
```

In this case, the `div` will inherit the `background-color` of its parent element.

**Pros:**

- Reduces the amount of code needed to style elements.
- Makes code easier to maintain, as you can change styles in one place.

**Cons:**

- Can lead to unexpected results if not fully understood, as styles may be applied to elements you didn't intend to style.
- Not all properties are inherited, which can lead to confusion.

**Overriding Inheritance:**

Inheritance can be overridden by specifying a style directly on a child element. Styles specified directly on an element always take precedence over inherited styles.

Furthermore, the `inherit` keyword can be used to force a property to be inherited, even if it's not by default. Conversely, the `initial` keyword can be used to apply the default value of a property, effectively preventing it from being inherited.