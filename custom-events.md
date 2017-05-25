# HTML 5 Custom Events

### Event From Child to Parent (Bubbling)

```javascript
element.addEventListener('event-name', handlerFunction);
```

### Event From Child to Parent (Capturing)

```javascript
element.addEventListener('event-name', handlerFunction, true);
```

### Posting An Event

```javascript
let event = new Event('something-happened');
element.dispatchEvent('something-happened');
```

### Creating An Event With Data

#### Standard

```javascript
let event = new CustomEvent('something-happened', {detail: data});
```

#### IE

```javascript
let event = document.createEvent('CustomEvent');
event.initCustomEvent(event, bubbles, cancelable, data);
```
