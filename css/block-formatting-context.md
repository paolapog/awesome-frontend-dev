A Block Formatting Context (BFC) is a part of the visual CSS rendering of a web page. It's the region in which the layout of block boxes occurs and the region that floats interact with. A BFC is a separate "context" in the layout, meaning it has its own set of rules for layout rendering.

**How it works:**

In a BFC, each box's left outer edge touches the left edge of the containing block. Vertically, boxes are stacked one after the other. The vertical distance between two sibling boxes is determined by the `margin` property. Margins between adjacent items can overlap.

A new BFC can be established by the following CSS properties:

- `float: left` or `float: right`
- `position: absolute` or `position: fixed`
- `display: inline-block`, `display: table-cell`, `display: table-caption`, `display: flex`, or `display: grid`
- `overflow: hidden`, `overflow: scroll`, or `overflow: auto`
- `contain: layout`, `contain: paint`, or `contain: strict`
- `column-count` or `column-width` other than `auto`
- `flex`, `flex-flow`, `flex-direction`, `flex-wrap`

**Use Cases:**

1. **Containing Floats:** In a BFC, the box only wraps around the content area, not the margin area. This can be used to prevent other content from wrapping around a floated element.

```css
.container {
  overflow: auto; /* creates new BFC */
}

.container img {
  float: left;
}
```

2. **Preventing Margin Collapse:** Margins of adjacent siblings can overlap. Creating a new BFC can prevent this.

```css
.container {
  overflow: auto; /* creates new BFC */
}

.container p {
  margin: 10px 0;
}
```

3. **Clearing Floats:** A common use of BFC is to clear floats. If a container has floated children, it will collapse upon itself because floats are removed from the normal flow. Creating a new BFC can clear the floats and expand the container to enclose the floated children.

```css
.container::after {
  content: "";
  display: table;
  clear: both;
}
```