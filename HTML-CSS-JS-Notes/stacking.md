# Stacking Card

```html
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta http-equiv="X-UA-Compatible" content="IE=edge" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Stacking Card</title>
    <link rel="stylesheet" href="styles.css" />
  </head>
  <body>
    <header><h1>Header</h1></header>
    <main>
      <div class="card">Card 1</div>
      <div class="card">Card 2</div>
      <div class="card">Card 3</div>
      <div class="card">Card 4</div>
    </main>
    <footer><h3>Footer</h3></footer>
  </body>
</html>
```

```css
@import url("https://fonts.googleapis.com/css2?family=Open+Sans:ital,wght@0,300;0,400;0,700;1,300;1,400;1,700&display=swap");
:root {
  --bg-color: rgba(0, 200, 122, 0.2);
}

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: "Open Sans", "Noto Sans", HelveticaNeueCyr, Helvetica, sans-serif;
}

body {
  background-color: var(--bg-color);
}

header,
footer {
  height: 200px;
  text-align: center;
  padding-top: 60px;
}

footer {
  height: 400px;
}

.card {
  --card-offset: 20px;

  height: 400px;
  max-width: 70%;
  position: sticky;
  top: calc(var(--card-offset) * 1);
  display: flex;
  justify-content: center;
  align-items: center;
  color: white;
  border: 5px solid black;
  background-color: red;
  margin: 12 auto;
}

.card:first-child {
  top: calc(var(--card-offset) * 2);
  background-color: rgba(20, 50, 200, 0.8);
}

.card:nth-child(2) {
  top: calc(var(--card-offset) * 5);
  background-color: green;
}

.card:nth-child(3) {
  top: calc(var(--card-offset) * 8);
  background-color: cadetblue;
}

.card:last-child {
  background-color: coral;
}
```
