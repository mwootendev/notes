# Custom Elements

[https://w3c.github.io/webcomponents/spec/custom/](Specification)

Extend HTMLElement or one of its subclasses.

Have 4 primary and one additional method:

- connectedCallback()
- disconnectedCallback()
- adoptedCallback()
- attributeChangedCallback(name, oldValue, newValue)
- static get observedAttributes() : string[]

```javascript
class CustomElement extends HTMLElement {
    static get observedAttributes() { return ['observed']; }
    attributeChangedCallback(name, oldVal, newVal) { this.innerHTML = newVal; }
}
```

Elements must be registered before their use:

```javascript
customElements.define('element-name', ElementPrototype);
```

Can extend existing Elements

```javascript
class MyButton extends HTMLButton {}

customElements.define('my-button', MyButton, [{extends: 'button'}]);
```

Extended components use the `is` attribute to specify the custom subclasses

```html
<button is="my-button">Text</button>
```

When created dynamically

```javascript
document.createElement('button', {is: 'my-button'});
```
