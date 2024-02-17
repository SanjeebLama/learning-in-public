# will-change css property

- The `will-change` CSS property hints to browsers how an element is expected to change (e.g., content, scroll position, opacity, etc.)
- Browsers may set up optimizations before an element is actually changed.
- These kinds of optimizations can increase the responsiveness of a page by doing potentially expensive work before they are actually required.
- This allows the browser to optimize the element’s rendering ahead of time, potentially resulting in better performance.

#### will-change can take four possible values:

- **auto** - browser will apply the optimizations
- **scroll-position** - indicates that the author expects to animate or change the scroll position of the element in the near future
- **contents** - indicates that the author expects to animate or change something about the element’s contents in the near future.
- **custom-indent** - indicates that the author expects to animate or change the property with the given name on the element in the near future.

```css
/* Keyword values */
will-change: auto;
will-change: scroll-position;
will-change: contents;
will-change: transform; /* Example of <custom-ident> */
will-change: opacity; /* Example of <custom-ident> */
will-change: left, top; /* Example of two <animatable-feature> */

/* Global values */
will-change: inherit;
will-change: initial;
will-change: revert;
will-change: revert-layer;
will-change: unset;
```

### More info

- https://developer.mozilla.org/en-US/docs/Web/CSS/will-change

- https://blog.logrocket.com/when-how-use-css-will-change/

- https://www.digitalocean.com/community/tutorials/css-will-change
