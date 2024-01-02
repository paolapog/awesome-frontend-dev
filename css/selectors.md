CSS selectors are the part of a CSS rule set that actually __selects the content__ you want to style. Let's break down the different types of selectors in CSS:

1. **Type selectors**: These are the most basic type of selector and they select elements by their node name.

```css
p {
  color: red;
}
```

The type selector `p` selects all paragraph elements.

2. **Class selectors**: These select elements based on the class attribute. They are denoted by a period (`.`) followed by the class name.

```css
.my-class {
  color: blue;
}
```

The class selector `.my-class` selects all elements with the class `my-class`.

3. **ID selectors**: These select elements based on the id attribute. They are denoted by a hash (`#`) followed by the id name.

```css
#my-id {
  color: green;
}
```

The ID selector `#my-id` selects the element with the id `my-id`.

4. **Attribute selectors**: These select elements based on an attribute or attribute value. 

```css
input[type="text"] {
  color: purple;
}
```

The attribute selector `input[type="text"]` selects all input elements with a type of "text".

5. **Pseudo-class selectors**: These select elements based on a certain state.

```css
a:hover {
  color: orange;
}
```

The pseudo-class selector `a:hover` selects all anchor tags when they are being hovered over.

6. **Pseudo-element selectors**: These select a part of an element.

```css
p::first-letter {
  font-size: 2em;
}
```

The pseudo-element selector `p::first-letter` selects the first letter of every paragraph.

7. **Combinator selectors**: These select elements based on a specific relationship between them. There are four types of combinators in CSS: descendant combinator (` `), child combinator (`>`), adjacent sibling combinator (`+`), and general sibling combinator (`~`).

```css
div p {
  color: teal;
}

div > p {
  color: teal;
}

div + p {
  color: teal;
}

div ~ p {
  color: teal;
}
```

The combinator selectors select a paragraph based on its relationship with a div.

8. **Universal selector (`*`)**: This selects all elements.

```css
* {
  margin: 0;
  padding: 0;
}
```

The universal selector `*` selects all elements and sets their margin and padding to 0.

9. **Grouping/Cascading selectors**: If you have elements with the same style definitions, like same color or font, you can group them together using a comma (`,`).

```css
h1, h2, p {
  color: navy;
}
```

The grouping selector `h1, h2, p` selects all `h1`, `h2`, and `p` elements and applies the same styles to them.

## Pseudo-classes vs pseudo-elements

Pseudo-classes and pseudo-elements are both special keywords used in CSS selectors, but they have different uses and syntax.

**Pseudo-classes**:

- Pseudo-classes are used to define a special state of an element. They can be used to style an element when it's hovered over, focused, active, checked, and more.
- Pseudo-classes are defined with a single colon (`:`), followed by the pseudo-class name. For example, `:hover`, `:focus`, `:active`, etc.
- Pseudo-classes can be used with any element, not just links.
- They are dynamic and can change when a user interacts with the page.

**Pseudo-elements**:

- Pseudo-elements are used to style specific parts of an element. They can be used to add special effects to some selectors.
- Pseudo-elements are defined with a double colon (`::`), followed by the pseudo-element name. For example, `::before`, `::after`, `::first-letter`, etc.
- Pseudo-elements create a new element for styling purposes, which becomes a child of the element it's applied to.
- They are static and do not change once the page has loaded.

Please, read also the [specifity](./specifity.md) part to better understand how to use selectors.