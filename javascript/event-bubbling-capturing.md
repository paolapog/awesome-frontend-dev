In JavaScript, __events__ are actions or occurrences that can activate specific functionality and lead to certain behaviors. Examples of such events include actions like "click" or "hover". You can establish event listeners that monitor these events and initiate the functionality you specify when these events occur.

## Event Propagation
Propagation in JavaScript pertains to the journey of events through the Document Object Model (DOM) tree. The DOM tree is a hierarchical structure that outlines the relationship between parent, child, and sibling elements. Propagation can be visualized as an electric current flowing through a wire until it reaches its target. The event traverses through each node in the DOM until it arrives at its final destination or is intentionally halted.

## Event Bubbling and Capturing
Bubbling and Capturing represent the two stages of event propagation. Simply put, bubbling **moves from the event target up to the root**, while capturing **moves from the root down to the event target**. To understand this, we need to define what a target and a root are.

The target is the DOM node where the event is triggered, such as a click on a button.

The root, on the other hand, is the topmost parent of the target, typically the document, which is a parent of the `<html>` element, which in turn is a (potentially distant) parent of your target element.

Capturing is less frequently used than bubbling, so our examples will focus on the bubbling phase. However, the `EventTarget.addEventListener()` method has an optional third parameter, `useCapture`, which controls the propagation phase. If `useCapture` is set to true, the listener will be in the capturing phase. The default is false, which applies it to the bubbling phase.

When an event is triggered, it propagates up to the root, activating every event handler of the same type along the way. For instance, if a button has a click event, during the bubbling phase, it will bubble up to the root, triggering every click event handler on its path. But, by calling `Event.stopPropagation()` will prevent further propagation through the DOM tree, and only run the event handler from which it was called.

```javascript
// HTML structure
<div id="parent">
  <button id="child">Click me</button>
</div>

// JavaScript
document.getElementById('parent').addEventListener('click', function() {
  console.log('Parent clicked!'); // This will run during the bubbling phase
}, false); // useCapture is set to false, so this listener is in the bubbling phase

document.getElementById('child').addEventListener('click', function(event) {
  console.log('Child clicked!'); // This will run first
  event.stopPropagation(); // This will stop the event from bubbling up to the parent
}, false); // useCapture is set to false, so this listener is in the bubbling phase
```
In this example, when you click the button (the child), the 'Child clicked!' message will be logged to the console. However, because `event.stopPropagation()` is called, the event will not bubble up to the parent, so 'Parent clicked!' will not be logged. If you comment out the `event.stopPropagation()` line and click the button again, both 'Child clicked!' and 'Parent clicked!' will be logged, demonstrating the event bubbling process. <br />
But, there is also another method: `Event.stopImmediatePropagation()`.

It is used to **prevent other listeners from being called**. If multiple listeners are attached to the same element for the same event type, they will be called in the order they were added. If `Event.stopImmediatePropagation()` is invoked during one such call, no remaining listeners will be called.
  
```javascript
// HTML structure
<button id="myButton">Click me</button>

// JavaScript
document.getElementById('myButton').addEventListener('click', function(event) {
  console.log('First listener called!');
  event.stopImmediatePropagation(); // This will prevent the second listener from being called
});

document.getElementById('myButton').addEventListener('click', function() {
  console.log('Second listener called!'); // This will not be logged because of stopImmediatePropagation()
});
```
In this example, when you click the button, only 'First listener called!' will be logged to the console. Even though there is a second event listener for the click event on the same button, it will not be called because `Event.stopImmediatePropagation()` is invoked in the first listener.
