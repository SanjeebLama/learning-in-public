| Name    | Desktop                                                                                                          | Mobile                                                                                                           |
| ------- | ---------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------- |
| Layout1 | ![image](https://github.com/SanjeebLama/learning-in-public/assets/51410633/ddf16f65-8298-4c7c-be28-fe73fb472feb) | ![image](https://github.com/SanjeebLama/learning-in-public/assets/51410633/92dfc8d0-4dca-4357-99af-fd0bf0078002) |

# Grid

- CSS Grid is a layout system in CSS for creating two-dimensional grid-based layouts.
- It simplifies the process of arranging elements on a webpage, offering precise control over layout design without complicated hacks.

### Parent Properties (Applied to Grid Container):

| Property                | Description                                                               |
| ----------------------- | ------------------------------------------------------------------------- |
| `display: grid`         | Defines a grid container and turns its children into grid items.          |
| `grid-template-columns` | Specifies the size of the columns in a grid layout.                       |
| `grid-template-rows`    | Specifies the size of the rows in a grid layout.                          |
| `grid-template-areas`   | Defines named grid areas which can be referenced when placing grid items. |
| `grid-gap`              | Sets the size of the gap between grid items.                              |
| `grid-row-gap`          | Sets the size of the gap between rows in a grid layout.                   |
| `grid-column-gap`       | Sets the size of the gap between columns in a grid layout.                |
| `grid-auto-columns`     | Sets the size of implicitly-created columns in a grid layout.             |
| `grid-auto-rows`        | Sets the size of implicitly-created rows in a grid layout.                |
| `grid-auto-flow`        | Defines how auto-placed items are placed in the grid layout.              |
| `justify-content`       | Aligns the grid along the inline (row) axis within the grid container.    |
| `align-content`         | Aligns the grid along the block (column) axis within the grid container.  |
| `place-content`         | A shorthand for `align-content` and `justify-content`.                    |

### Child Properties (Applied to Grid Items):

| Property       | Description                                                                           |
| -------------- | ------------------------------------------------------------------------------------- |
| `grid-column`  | Specifies where an item should be placed in terms of the grid columns it should span. |
| `grid-row`     | Specifies where an item should be placed in terms of the grid rows it should span.    |
| `justify-self` | Aligns a grid item along the inline (row) axis within its grid area.                  |
| `align-self`   | Aligns a grid item along the block (column) axis within its grid area.                |
| `place-self`   | A shorthand for `align-self` and `justify-self`.                                      |

These properties allow for the creation of complex grid layouts and the precise placement of grid items within them by controlling the grid container and individual grid items separately.

## Layout 1

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Simple Grid Example</title>
    <link rel="stylesheet" href="styles.css" />
  </head>
  <body>
    <div class="grid-container">
      <nav>Navbar</nav>
      <main>Main</main>
      <div class="sidebar">Sidebar</div>
      <div class="content1">Content 1</div>
      <div class="content2">Content 2</div>
      <div class="content3">Content 3</div>
      <footer>footer</footer>
    </div>
  </body>
</html>
```

```css
:root {
  --main-radius: 5px;
  --main-padding: 5px;

  --blue: #2f3c7e;
  --pink: #ff69b4;
  --charcoal: #101820;
  --bright-yellow: #fee715;
  --teal: #008080;
  --coral: #ff7f50;
  --slate-gray: #708090;
  --magenta: #ff00ff;
  --goldenrod: #daa520;
  --lavender: #e6e6fa;
  --olive: #808000;
  --ruby: #e0115f;
  --sky-blue: #87ceeb;
  --peach: #ffdab9;
}

body {
  box-sizing: border-box;
  margin: 0;
}

.grid-container {
  height: 100vh;
  display: grid;
  grid-template-columns: 1fr 1fr 1fr 1fr;
  grid-template-rows: 0.2fr 1.5fr 1.2fr 0.8fr;
  grid-template-areas:
    "nav nav nav nav"
    "sidebar main main main"
    "sidebar content1 content2 content3"
    "sidebar footer footer footer";
  grid-gap: 0.2rem;
  text-align: center;
  color: white;
}

.grid-container > * {
  border: 1px solid #000;
  border-radius: var(--main-radius);
  padding-top: var(--main-padding);
}

nav {
  grid-area: nav;
  background: var(--blue);
}

.sidebar {
  grid-area: sidebar;
  background: var(--pink);
}

main {
  grid-area: main;
  background: var(--teal);
}

.content1 {
  grid-area: content1;
  background: var(--coral);
}

.content2 {
  grid-area: content2;
  background: var(--coral);
}

.content3 {
  grid-area: content3;
  background: var(--coral);
}

footer {
  grid-area: footer;
  background: var(--ruby);
}

@media only screen and (max-width: 640px) {
  .grid-container {
    grid-template-columns: 1fr;
    grid-template-rows: 0.4fr 0.4fr 2.2fr 1.2fr 1.2fr 1.2fr 1fr;
    grid-template-areas:
      "nav"
      "sidebar"
      "main"
      "content1"
      "content2"
      "content3"
      "footer";
  }
}
```

## Resources and References:

1. https://www.youtube.com/playlist?list=PL4cUxeGkcC9hk02lFb6EkdXF2DYGl4Gg4

2. https://www.youtube.com/watch?v=68O6eOGAGqA&t=5s

### Layout

- https://www.youtube.com/watch?v=i1FeOOhNnwU

- https://www.youtube.com/watch?v=hs3piaN4b5I

- https://www.youtube.com/watch?v=3elGSZSWTbM
