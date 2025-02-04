---
title: Selection.removeAllRanges()
slug: Web/API/Selection/removeAllRanges
page-type: web-api-instance-method
browser-compat: api.Selection.removeAllRanges
---

{{ ApiRef("DOM") }}

The **`Selection.removeAllRanges()`** method removes all ranges from the selection, leaving the {{domxref("Selection.anchorNode", "anchorNode")}} and {{domxref("Selection.focusNode","focusNode")}} properties equal to `null` and nothing selected. When this method is called, a {{domxref("Document/selectionchange_event", "selectionchange")}} event is fired at the document.

> **Note:** This method is an alias for the {{domxref("Selection.empty()")}} method.

## Syntax

```js-nolint
removeAllRanges()
```

### Parameters

None.

### Return value

None ({{jsxref("undefined")}}).

## Examples

This example displays a message when something is selected on the page or not. It does this by listening to the {{domxref("Document/selectionchange_event", "selectionchange")}} event on the document. There also is a button that clears any selection by calling `Selection.removeAllRanges()`. When this happens, the selection is changed and the message is updated.

```html
<p>
  Lorem ipsum dolor sit amet, consectetur adipiscing elit. Suspendisse laoreet
  urna eget sapien venenatis, eget facilisis diam mattis.
</p>
<button>Clear selection</button>
<pre id="log"></pre>
```

```js
const log = document.getElementById("log");

// The selection object is a singleton associated with the docuemnt
const selection = document.getSelection();

// Logs if there is a selection or not
function newSelectionHandler() {
  if (selection.rangeCount !== 0) {
    log.textContent = "Some text is selected.";
  } else {
    log.textContent = "No selection on this document.";
  }
}

document.addEventListener("selectionchange", () => {
  newSelectionHandler();
});

newSelectionHandler();

// The button cancel all selection ranges
const button = document.querySelector("button");
button.addEventListener("click", () => {
  selection.removeAllRanges();
});
```

{{EmbedLiveSample("Examples", "100%", "200px")}}

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- {{domxref("Selection.empty()")}}
- {{domxref("Document/selectionchange_event", "selectionchange")}}
