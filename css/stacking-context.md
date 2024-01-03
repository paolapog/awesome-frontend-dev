## Stacking context

A stacking context in CSS is formed when an element has any of the following properties:

1. `position: absolute` or `position: relative` with a `z-index` value other than `auto`.
2. `position: fixed` or `position: sticky`.
3. A `flex` container with a `z-index` value other than `auto` (`display: flex` or `display: inline-flex`).
4. `opacity` value less than 1.
5. `transform`, `filter`, `perspective`, `clip-path`, `mask`, `mask-image`, `mask-border` properties with any value other than `none`.
6. `isolation: isolate`.
7. `mix-blend-mode` with any value other than `normal`.
8. A `z-index` value of `auto` and `contain: layout`, `contain: paint`, or `contain: strict`.
9. `will-change` with a value specifying any property that would create a stacking context on non-initial value.

When a new stacking context is formed, it confines the z-indices of its children to that context. This means that an element with `z-index: 1000` inside a stacking context won't appear above an element with `z-index: 1` that's outside of that stacking context, even though 1000 is greater than 1. This is a common source of confusion when working with `z-index` and stacking contexts.

## Stacking order

The stacking order in CSS is the order in which elements are rendered on the z-axis (the axis that comes out of the screen towards the viewer). It determines what order elements are drawn in when they overlap.

The stacking order is influenced by several factors:

1. **Positioning and z-index:** Positioned elements (those with `position: relative`, `position: absolute`, `position: fixed`, or `position: sticky`) with a defined `z-index` value are rendered in order of their `z-index` values, from lowest to highest. Elements with a higher `z-index` appear on top of elements with a lower `z-index`.

2. **Parent-child relationships:** Child elements are always rendered in front of their parent. So, even if a parent has a higher `z-index`, it will not appear in front of its child.

3. **Order in the HTML:** If two elements have the same `z-index` (or no `z-index`), the one that comes later in the HTML is rendered on top.

4. **Stacking context:** Certain properties create new stacking contexts, such as `opacity` less than 1, `transform` not none, `filter` not none, etc. Elements within a stacking context are rendered together before being rendered with the rest of the page, which can affect the stacking order.
