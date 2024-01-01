The term "document flow" in CSS refers to the __arrangement and positioning__ of elements in the document as they appear in the HTML source code. By default, elements in an HTML document flow from top to bottom and left to right, in the same order they appear in the document's source code.

Types of positioning that can affect the document flow:

1. **Normal Flow (Static Positioning)**: This is the default positioning model. Elements in normal flow follow the order they appear in the source code. Block-level elements stack vertically, one after the other, while inline elements sit within the same line, flowing left to right.

2. **Relative Positioning**: An element with relative positioning is slightly offset from its normal position in the document flow, but without changing the layout around it. The space it would normally occupy is preserved.

3. **Absolute Positioning**: An element with absolute positioning is removed from the document flow. It doesn't affect the position of other elements; they behave as if the absolutely positioned element doesn't exist. It's positioned relative to its nearest positioned ancestor (instead of positioned relative to the viewport, like fixed).

4. **Fixed Positioning**: An element with fixed positioning is also removed from the document flow. It's positioned relative to the viewport, meaning it stays in the same place even if the page is scrolled.

5. **Sticky Positioning**: A stickily positioned element is treated as relatively positioned until its containing block crosses a specified threshold (such as setting top to value other than auto) within its flow root.

The `display` property (block, inline, inline-block) and `float` property can also affect the document flow. 
For example, a floated element is taken out of the normal flow and shifted to the left or right, while other elements wrap around it.