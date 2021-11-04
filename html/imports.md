# HTML Imports

[http://w3c.github.io/webcomponents/spec/imports/](Specification)

Use the <link> tag with a relationship of "import" and "href" with address.

```html
<link rel="import" href="/path/to/file.html" />
```

Also accepts "async" attribute for asynchronous loading.

HTML content is available under the "import" field.

```javascript
var linkElem = doc.querySelector('link');
linkElem.import; // imported document
```
