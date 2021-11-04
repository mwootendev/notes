# Shadow DOM

## Links

(https://www.w3.org/TR/shadow-dom/)[W3 Shadow DOM]

##  

Adding a Shadow DOM subtree to an element.

```javascript
element.attachShadow({mode: 'open'});
```

## Including Content from Outside the Shadow DOM

Content can be placed into the Shadow DOM through the use of the HTML `<slot>` element.

## Styling

One of the key benefits of the Shadow DOM is that it scopes its styles to within the shadow tree, with styles from the parent document not affecting the shadow DOM content and styles from within the Shadow DOM not leaking into the parent document. CSS custom properties will be applied within the Shadow DOM's styles, and provide a means for the parent document to style Shadow DOM content. Using this approach, elements within the Shadow DOM can choose which style properties should be available to the parent document.
