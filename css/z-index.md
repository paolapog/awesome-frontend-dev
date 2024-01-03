The `z-index` property in CSS controls the vertical stacking order of elements that overlap. As such, `z-index` doesn't affect layout but rather, it affects the visibility of elements when they overlap. It only works on positioned elements (`position: absolute`, `position: relative`, `position: fixed`, or `position: sticky`).

The `z-index` property accepts integer values (positive, zero, or negative), which represent the position of the element along the z-axis:

- An element with a higher `z-index` will be displayed on top of an element with a lower `z-index`.
- If elements have the same `z-index`, the element that is later in the HTML will appear on top.
- Elements with no `z-index` property will appear beneath elements with `z-index` set (even if it's negative).

**Use Cases:**

- **Modals/Popups**: When you want a modal to appear over other content, you can give it a high `z-index`.
- **Dropdown Menus**: Similar to modals, dropdown menus should appear above other content, so they often have a high `z-index`.
- **Sticky Headers/Footers**: If you want a sticky header or footer to appear above other content when scrolling, you can use `z-index`.

**Pros:**

- Allows control over the [stacking order](./stacking-context.md) of elements, which is crucial for certain UI elements like modals, tooltips, dropdown menus, and sticky headers/footers.

**Cons:**

- If not managed properly, `z-index` can lead to confusing stacking contexts, where an element with a higher `z-index` might appear below an element with a lower `z-index` due to being in a different stacking context.
- It can lead to magic number problems, where arbitrary `z-index` values are used to get the desired effect, but it's unclear what the values mean or how changing them might affect the rest of the document.
- It only works on positioned elements, so it requires the element to have a `position` value other than `static`.
