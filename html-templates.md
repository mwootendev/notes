# HTML Templates

[HTML Templates Standard](https://html.spec.whatwg.org/multipage/scripting.html#the-template-element)

``` html
<template id="my-template"><span>Template Content</span></template>
```

HTML Templates do not have any nested nodes. The content inside the template is referenced by the `template` property on the element.

``` JavaScript
const templateElement = document.querySelector('#my-template');
const templateContent = templateElement.content;
const newElement = document.importNode(templateContent);
const clonedElement = templateContent.cloneNode(true);
```
