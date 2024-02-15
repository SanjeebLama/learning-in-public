| Name    | Preview                                                                                                          | 
| ------- | ---------------------------------------------------------------------------------------------------------------- 
| Layout1 | ![image](https://github.com/SanjeebLama/learning-in-public/assets/51410633/ddf16f65-8298-4c7c-be28-fe73fb472feb) | 
| Layout2 |![image](https://github.com/SanjeebLama/learning-in-public/assets/51410633/970a2fd2-cef9-4815-807d-b346dc301097) |
| Layout3 (Nested Grid) |![image](https://github.com/SanjeebLama/learning-in-public/assets/51410633/2971dce7-e176-4d38-87a2-4e288ff80de3)|
| Layout4 (Masonry) | ![image](https://github.com/SanjeebLama/learning-in-public/assets/51410633/8ce8196f-572b-4a18-beff-c26003aa35b9)|

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
| Name    | Desktop                                                                                                          | Mobile                                                                                                           |
| ------- | ---------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------- |
| Layout1 | ![image](https://github.com/SanjeebLama/learning-in-public/assets/51410633/ddf16f65-8298-4c7c-be28-fe73fb472feb) | ![image](https://github.com/SanjeebLama/learning-in-public/assets/51410633/92dfc8d0-4dca-4357-99af-fd0bf0078002) |

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

## Layout 2
| Name    | Preview                                                                                                          | 
| ------- | ---------------------------------------------------------------------------------------------------------------- |
| Layout2 |![image](https://github.com/SanjeebLama/learning-in-public/assets/51410633/970a2fd2-cef9-4815-807d-b346dc301097) |

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Simple Grid Example 2</title>
    <link rel="stylesheet" href="styles.css" />
  </head>
  <body>
    <main class="grid-container">
      <div class="">1</div>
      <div class="">2</div>
      <div class="">3</div>
      <div class="">4</div>
      <div class="">5</div>
      <div class="">6</div>
    </main>
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
  margin: 30px;
  background-color: #e6e6fa;
}

.grid-container {
  background-color: rgba(0, 0, 30, 0.1);
  max-width: 900px;
  margin: 0 auto;
  display: grid;
  row-gap: 6px;
  column-gap: 4px;
  grid-template-columns: repeat(6, 1fr);
  grid-template-rows: 100px 200px 300px;

  /* by default */
  justify-items: stretch;
  align-items: stretch;
}

.grid-container > * {
  border: 1px solid #101820;
  padding: 4px;
  text-align: center;
  color: white;
}

div:nth-child(1) {
  grid-column: 1/3;
  justify-self: start;
  background-color: var(--goldenrod);
}

div:nth-child(2) {
  grid-column: span 3;
  align-self: center;
  background-color: var(--coral);
}

div:nth-child(3) {
  justify-self: end;
  align-self: start;
  background-color: var(--blue);
}

div:nth-child(4) {
  grid-column: 2/6;
  background-color: var(--pink);
}

div:nth-child(5) {
  grid-column: span 3;
  align-self: flex-end;
  background-color: var(--olive);
}

div:nth-child(6) {
  grid-column: span 3;
  align-self: center;
  background-color: var(--teal);
}

```
## Layout 3
| Desktop  | Tablet  | Mobile  | 
| ---------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------- |
|![image](https://github.com/SanjeebLama/learning-in-public/assets/51410633/2971dce7-e176-4d38-87a2-4e288ff80de3)|![image](https://github.com/SanjeebLama/learning-in-public/assets/51410633/35a43109-d02b-4907-b4b3-67fccae5818f)|![image](https://github.com/SanjeebLama/learning-in-public/assets/51410633/32eb8dfc-ce4a-40d9-a055-6b3eb9cc5887)|



```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Simple Grid Example 3</title>
    <link rel="stylesheet" href="styles.css" />
  </head>
  <body>
    <header>
      <h1>Buddhist Monk</h1>
    </header>
    <main class="grid-container">
      <article class="featured">
        <img
          src="https://images.unsplash.com/photo-1558868540-3b5e8ca26dc2?q=80&w=1770&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D"
          alt="Buddhist Monk Sitting near lake"
          class="featured img"
        />
        <div class="">
          <h2>Exploring the Life of a Buddhist Monk</h2>
          <p>
            Dive into the tranquil existence of Buddhist monks as they embrace
            simplicity, meditation, and detachment from worldly desires in
            pursuit of spiritual enlightenment.
          </p>
        </div>
      </article>

      <article>
        <img
          src="https://images.unsplash.com/flagged/photo-1575253024459-3150df1a24bc?q=80&w=1770&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D"
          alt="Monks crossing the bridge"
        />
        <div class="">
          <h2>The Travelling Monks</h2>
          <p>
            Embark on a spiritual odyssey with travelling monks who wander
            across landscapes, spreading teachings, and seeking enlightenment.
          </p>
        </div>
      </article>

      <article>
        <img
          src="https://images.unsplash.com/photo-1529546628049-75f334518ab5?q=80&w=1769&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D"
          alt="Monks Praying"
        />
        <div class="">
          <h2>The Daily Rituals</h2>
          <p>
            Discover the disciplined lifestyle of Buddhist monks, from pre-dawn
            meditations to alms rounds and communal chanting, as they follow
            ancient traditions on their path to inner peace.
          </p>
        </div>
      </article>

      <article>
        <img
          src="https://images.unsplash.com/photo-1542319054772-19bc40f49235?q=80&w=1770&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D"
          alt="Children monk studying"
        />
        <div class="">
          <h2>Journey of Children Monks</h2>
          <p>
            Explore how these children embrace Buddhist teachings, meditation
            practices, and traditional rituals, shaping their path towards a
            life of dedication and wisdom from an early age.
          </p>
        </div>
      </article>
    </main>
  </body>
</html>

```


```css
@import url("https://fonts.googleapis.com/css2?family=Poppins:wght@200;400;500;600;800&family=VT323&display=swap");

body {
  margin: 20px;
  font-family: "Poppins";
  background: #d1dedd;
}
h1,
h2,
h3 {
  color: #767f7e;
}
p {
  color: #828b8a;
  text-align: left;
}

header {
  max-width: 1200px;
  margin: 40px auto;
  border-bottom: 1px solid #bbc7c7;
}

.grid-container {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 60px;
  max-width: 1200px;
  margin: 20px auto;
}

article.featured {
  grid-column: span 3;
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 60px;
  align-items: center;
  border-bottom: 1px solid #bbc7c7;
  padding-bottom: 40px;
}

article img {
  width: 100%;
  border: 4px solid #fff;
  border-radius: 8px;
}

article p h3 {
  margin: 20px 10px;
}

@media screen and (max-width: 980px) {
  article {
    grid-column: span 3;
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 60px;
    align-items: center;
  }
}

@media screen and (max-width: 760px) {
  article,
  article.featured {
    display: block;
    margin: 0 20px;
  }
}

```

## Layout 4 (Masonry)
| Desktop  | Tablet  | Mobile  | 
| ---------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------- |
| ![image](https://github.com/SanjeebLama/learning-in-public/assets/51410633/8ce8196f-572b-4a18-beff-c26003aa35b9)|![image](https://github.com/SanjeebLama/learning-in-public/assets/51410633/97bdc23a-519a-497f-bf88-18ed4f487318)|![image](https://github.com/SanjeebLama/learning-in-public/assets/51410633/a7631ad2-682a-4999-a441-08cb700b329c)|

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Simple Grid Example 3</title>
    <link rel="stylesheet" href="styles.css" />
  </head>
  <body>
    <header>
      <nav>
        <a href="/">Home</a>
        <a href="/">Articles</a>

        <h1>
          <div class="">Express</div>
          <div class="">Yourself</div>
        </h1>
        <a href="/">Guides</a>
        <a href="/">Contact</a>
      </nav>
    </header>

    <main>
      <div class="short">
        <h3>A note about style</h3>
        <p>
          Lorem ipsum dolor sit, amet consectetur adipisicing elit. Quisquam,
          reprehenderit.
        </p>
        <a href="">Read more</a>
      </div>
      <div class="tall">
        <img
          src="https://plus.unsplash.com/premium_photo-1706727290844-088603c0a79c?q=80&w=1887&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D"
          alt="model"
        />
      </div>
      <div class="short">
        <h3>A note about style</h3>
        <p>
          Lorem ipsum dolor sit, amet consectetur adipisicing elit. Quisquam,
          reprehenderit.
        </p>
        <a href="">Read more</a>
      </div>
      <div class="tall">
        <img
          src="https://images.unsplash.com/photo-1707834831436-a61faa9e2f2c?q=80&w=1887&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D"
          alt="model"
        />
      </div>
      <div class="tall">
        <img
          src="https://plus.unsplash.com/premium_photo-1707793860917-3f7022a70dce?q=80&w=1887&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D"
          alt="model"
        />
      </div>
      <div class="tall">
        <h3>A note about style</h3>
        <p>
          Lorem ipsum dolor sit, amet consectetur adipisicing elit. Quisquam,
          reprehenderit.
        </p>
        <p>
          Lorem ipsum dolor, sit amet consectetur adipisicing elit. Quas
          perspiciatis natus sit dicta repellendus quia mollitia. Voluptas ullam
          ipsa dolorem.
        </p>
        <p>
          Lorem ipsum dolor, sit amet consectetur adipisicing elit. Esse
          accusamus possimus asperiores fugiat at nostrum odio repellendus
          voluptates. Iusto asperiores voluptate similique maiores ut omnis
          dolores corporis, tenetur excepturi quis?
        </p>
        <a href="">Read more</a>
      </div>
      <div class="short">
        <h3>A note about style</h3>
        <p>
          Lorem ipsum dolor sit, amet consectetur adipisicing elit. Quisquam,
          reprehenderit.
        </p>
        <a href="">Read more</a>
      </div>
      <div class="tall">
        <img
          src="https://plus.unsplash.com/premium_photo-1700802066668-d3aa7fef7069?q=80&w=1887&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D"
          alt="model"
        />
      </div>
      <div class="short">
        <h3>A note about style</h3>
        <p>
          Lorem ipsum dolor sit, amet consectetur adipisicing elit. Quisquam,
          reprehenderit.
        </p>
        <a href="">Read more</a>
      </div>
      <div class="short">
        <h3>A note about style</h3>
        <p>
          Lorem ipsum dolor sit, amet consectetur adipisicing elit. Quisquam,
          reprehenderit.
        </p>
        <a href="">Read more</a>
      </div>
    </main>
  </body>
</html>

```


```css
@import url("https://fonts.googleapis.com/css2?family=Poppins:wght@200;400;500;600;800&family=VT323&display=swap");

body {
  margin: 0px;
  font-family: "Poppins";
  background: #f7f7f7;
}

header {
  background: #fff;
  padding: 10px;
}

nav {
  max-width: 1400px;
  margin: 0 auto;
  display: grid;
  grid-template-columns: repeat(5, 1fr);
  text-align: center;
  align-items: center;
}

nav h1 {
  text-transform: uppercase;
  line-height: 1em;
}

nav h1 div:first-child {
  font-weight: 800;
  letter-spacing: 1.5px;
}

nav h1 div:last-child {
  font-weight: 400;
}

nav a {
  text-decoration: none;
  color: #333;
}

main {
  max-width: 1200px;
  margin: 60px auto;
  padding: 20px;

  display: grid;
  grid-template-columns: repeat(3, 1fr);

  /* grid-auto-rows: Sets the size of implicitly-created rows in a grid layout.  */
  grid-auto-rows: 250px;
  gap: 30px;

  /* border: 4px solid saddlebrown; */
}

main div {
  overflow: hidden;
  background: #fff;
  border-radius: 6px;
  border: 16px solid #fff;
  box-shadow: 3px 3px 5px rgba(0, 0, 0, 0.05);
}

main img {
  min-width: 100%;
  height: 100%;
}

main .short {
  grid-row: span 1;
}

main .tall {
  grid-row: span 2;
}

@media screen and (max-width: 960px) {
  main {
    grid-template-columns: 1fr 1fr;
  }
}

@media screen and (max-width: 620px) {
  main {
    grid-template-columns: 1fr;
    max-width: 400px;
    margin-top: 20px;
  }
  nav {
    grid-template-columns: repeat(4, 1fr);
  }
  nav h1 {
    grid-column: 1 / span 4;
    grid-row: 1;
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
