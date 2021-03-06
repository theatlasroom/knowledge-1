# Immutable CSS

_The "C" is for "Composable"._

An approach to css which favours composition over cascading.

## media queries

This is one of the big questions around immutable css. If we can't change the meaning of a class, how do we get it to display adaptively to different screen sizes?

Here's what I've been trying lately:

- define atoms for various style aspects
- compose them together
- we can also compose atoms media queries

eg.

```jsB
const cmz = require('cmz')

const mediumText = cmz(`
  font-size: 3rem
`)

const largeText = cmz(`
  font-size: 5rem
`)

const c = cmz([
  mediumText,
  atMedia({ min-width: 550 }, largeText)
])

// <div class="${c}">...</div>
```

`atMedia` above actually generates a new css class on-demand, wrapped in a media query:

```css
@media (min-width: 550px) {
  .largeTextWhenMinWidth550 {
    font-size: 5rem;
  }
}
```

Inspecting the DOM, it looks like this:

```html
<div class="mediumText largeTextWhenMinWidth550">...</div>
```

So we can still have "conditional application" of atoms, without mutating them.
