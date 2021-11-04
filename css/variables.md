# CSS Variables

## Links

[W3 Schools CSS Variables](https://www.w3schools.com/css/css3_variables.asp)

[Mozilla Using Custom CSS Variables](https://developer.mozilla.org/en-US/docs/Web/CSS/Using_CSS_variables)

[CSS Working Group CSS Variables Draft](https://drafts.csswg.org/css-variables/)

[W3C CSS Variables Specification](https://www.w3.org/TR/css-variables-1/)

## Custom Properties

Custom properties are case sensitive, user-defined properties that begin with `--` and have a valid CSS identfier. They provide a means for CSS authors to define meaningful names related to values. Custom properties are subject to the normal cascade rules when identifying the value of the custom property.

```css
--theme-primary-color: #FF0000;
--theme-secondary-color: #00FFFF;

.header {
  --theme-primary-color: #00FF00;
}
```

## `var()` Function

The `var()` function is used to replace a value with the value assigned to a custom property. The `var()` function optionally accepts a second argument for a default (or fallback) value if the custom property is not declared or is invalid.

The general for for the `var()` function is `var(<custom property name>[, <default value>])`.

```css
background-color: var(--theme-primary-color, #FFFFFF);
color: var(--theme-secondary-color, #000000);
```

The `var()` function must also replace an entire CSS token, for instance `width: var(--header-width)px;` is not valid. The unit must either be included in the custom property or `calc()` can be used to convert the unit, e.g. `width: calc(var(--header-width) * 1px);`.

`var()` functions themselves can be used as fallback values, allowing for different levels of configuration. For instance, if a specific component does not have a custom property assigned, it could try to fall back to a more generic theme custom property.

```css
background-color: var(--my-component-bg-color, var(--theme-background-color, white));
```


