# HTML Slots

[HTML Slot Specification](https://html.spec.whatwg.org/multipage/scripting.html#the-slot-element)

[Slot MDN Page](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/slot)

A `<slot>` is a named element that can be used as a placeholder for other content to be "slotted" in later.

A slot will display any nested nodes from the slot's declaration, unless there is named content to fill the slot, in which the slot's content will be replaced with the specified content.

The `<slot>` element has a single attribute, `name`, that is used to provide the name of the slot.

``` html
<slot name="my-slot">Default content</slot>
```

Slots can then be referenced by their name using a `slot` attribute on the content to be inserted into the `<slot>` location.

``` html
<template id="example-content">
  <style>
    code {
      color: #CCCCCC;
    }
  </style>
  <code><pre><slot name="example">Default</slot></pre></code>
</template>
```

``` JavaScript
class ExampleContentElement extends HTMLElement {

  constructor() {
    super();
    
    const template = document.querySelector('#example-content').content;
    this.attachShadow({mode: 'open'}).appendChild(template.cloneNode(true));
  }

}
customElements.define('example-content', ExampleContentElement);
```

``` html
<example-content>
  <span slot="example">console.log('Hello, World');</span>
</example-content>
```
