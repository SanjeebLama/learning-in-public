### Inset

<details>
  <summary> <b>Click to view the answer.</b> </summary>

- The `inset` CSS property is a shorthand property that combines the `top`, `right`, `bottom`, and `left` properties, defining the offset of a positioned element.

- It is commonly used with absolutely positioned elements, allowing precise control over their placement within their containing element.

**The syntax for `inset` property is:**

```css
inset: <top> <right> <bottom> <left>;
```

Where:

- `<top>`: Specifies the offset from the top edge.
- `<right>`: Specifies the offset from the right edge.
- `<bottom>`: Specifies the offset from the bottom edge.
- `<left>`: Specifies the offset from the left edge.

Each value can be specified in pixels, percentages, ems, rems, or any other CSS length unit.

Here's an example to demonstrate the usage of the `inset` property:

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Inset Property Example</title>
    <style>
      .box {
        position: absolute;
        width: 100px;
        height: 100px;
        background-color: coral;
        inset: 20px 50px 20px 50px; /* Top 20px, Right 50px, Bottom 20px, Left 50px */
      }
    </style>
  </head>
  <body>
    <div class="box"></div>
  </body>
</html>
```

- In this example, we have a `div` element with the class `box`.

- The `box` class is styled to have absolute positioning and a width and height of 100 pixels each.

- The background color is set to coral.

- The `inset` property is used to position the box 20 pixels from the top, 50 pixels from the right, 20 pixels from the bottom, and 50 pixels from the left within its containing element.

</details>
