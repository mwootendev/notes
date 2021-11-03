#css #methodology

# Scalable and Modular Architecture for CSS

Breaks CSS rules into five categories:

1. Base
2. Layout
3..Module
4. State
5. Theme

Each category has its own guidelines and rules. 

## Base Rules

The default rules for basic HTML elements. Often like a reset to ensure that `<div>` is a `block`, default margin and padding are 0, etc.

## Layout Rules

Used to divide the page into different sections (header, sidebar, footer, etc.).
It is recommended that CSS selectors for layout begin with `l-` or `layout-` to indicate that they are layout rules.

## Module Rules

Modules are reusable graphical elements (cards, accordion, etc.). The provide the content displayed in the layout. 

The recommendation is for module rules to be the name of the module. For instance, a card module may use rules that start with `.card`. Any subelemnts will be prefixed with the module name and a hyphen (i.e. `.card-`).

## State Rules

The state rules apply to modules and layouts when they are in a specific state. For instance, an accordion may have an "expanded" state. Buttons may be "active" or "indactive". A form may be in an "error" state.
The recommendation is to prefix state rules wtth `is-`. Examples may include `is-hidden` or `is-collapsed`.

## Theme Rules

Additional rules for lauouts or modules to change their appearance.
