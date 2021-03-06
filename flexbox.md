# CSS Flexbox

## Links

[W3C Flexbox Specification](https://www.w3.org/TR/css-flexbox-1/)

[CSS Tricks Flexbox Guide](https://css-tricks.com/snippets/css/a-guide-to-flexbox/)

[W3 Schoole Flexbox Guide](https://www.w3schools.com/css/css3_flexbox.asp)


## Container

### `display`

Specifies that the element is a flexbox container.

| Property      | Description                                                                          |
| ------------- | ------------------------------------------------------------------------------------ |
| `flex`        | Specifies that the container is a block element and its contents will use flexbox.   |
| `inline-flex` | Specifies that the container is an inline element and its contents will use flexbox. |

### `flex-direction`

Specifies the direction that items within the flexbox should be laid out.

| Property         | Description                                                                          |
| ---------------- | ------------------------------------------------------------------------------------ |
| `row`            |  |
| `column`         |  |
| `row-reverse`    |  |
| `column-reverse` |  |

### `flex-wrap`

Specifies how the contents of the flexbox can wrap.

| Property       | Description                                                                          |
| -------------- | ------------------------------------------------------------------------------------ |
| `wrap`         |  |
| `nowrap`       |  |
| `wrap-reverse` |  |

### `flex-flow`

Shorthand for specifying `flex-direction` and `flex-wrap`.

``` css
flex-flow: column nowrap;
```


### `justify-content`

TODO

| Property        | Description                                                                          |
| --------------- | ------------------------------------------------------------------------------------ |
| `flex-start`    |  |
| `flex-end`      |  |
| `center`        |  |
| `space-around`  |  |
| `space-between` |  |

### `align-items`

TODO

| Property     | Description                                                                          |
| ------------ | ------------------------------------------------------------------------------------ |
| `flex-start` |  |
| `flex-end`   |  |
| `center`     |  |
| `stretch`    |  |
| `baseline`   |  |

### `align-content`

TODO

| Property        | Description                                                                          |
| --------------- | ------------------------------------------------------------------------------------ |
| `flex-start`    |  |
| `flex-end`      |  |
| `center`        |  |
| `stretch`       |  |
| `space-around`  |  |
| `space-between` |  |

## Items

### Order

TODO

| Property | Description                                                                          |
| -------- | ------------------------------------------------------------------------------------ |
| `#`      |  |

### flex-grow

TODO

| Property | Description                                                                          |
| -------- | ------------------------------------------------------------------------------------ |
| `#`      |  |

### flex-shrink

TODO

| Property | Description                                                                          |
| -------- | ------------------------------------------------------------------------------------ |
| `#`      |  |

### flex-basis

TODO

| Property      | Description                                                                          |
| ------------- | ------------------------------------------------------------------------------------ |
| `#`           |  |
| `auto`        |  |
| `main-size`   |  |
| `content`     |  |
| `max-content` |  |
| `min-content` |  |
| `fit-content` |  |

### flex

Shorthand for specifying `flex-grow`, `flex-shrink`, and `flex-basis`.

``` css
flex: 2 1 auto;
```

### `align-self`

TODO

| Property     | Description                                                                          |
| ------------ | ------------------------------------------------------------------------------------ |
| `auto`       |  |
| `flex-start` |  |
| `flex-end`   |  |
| `center`     |  |
| `stretch`    |  |
| `baseline`   |  |
