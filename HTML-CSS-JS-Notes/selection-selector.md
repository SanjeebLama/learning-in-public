# Selection selector

- The `::selection` selector matches the portion of an element that is selected by a user.
- Only a few CSS properties can be applied to the `::selection` selector:
  - color,
  - background,
  - cursor, and
  - outline.

```css
::selection {
  css declarations;
}

```

```html
<!DOCTYPE html>
<html>
  <head>
    <style>
      ::selection {
        color: red;
        background: yellow;
      }
    </style>
  </head>
  <body>
    <h1>Select some text on this page:</h1>

    <p>This is a paragraph.</p>
    <div>This is some text in a div element.</div>
  </body>
</html>
```
