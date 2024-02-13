# Pig Emoji

<center>

![Pig](https://github.com/SanjeebLama/learning-in-public/assets/51410633/5c864a93-c24b-4994-85aa-24c012f59ddf)

</center>


## What I Learned
- **It was tougher than I thought but simpler than Robot emoji:** I got to revise about the positioning of the elements and pseudo-classes.
  
## HTTML Snippets
```html
    <div class="head">
      <div class="">
        <div class="ear"></div>
        <div class="ear"></div>
      </div>

      <div class="">
        <div class="eye">
          <div class="pupil"></div>
        </div>
        <div class="eye">
          <div class="pupil"></div>
        </div>
      </div>

      <div class="nose">
        <div class="nostril"></div>
        <div class="nostril"></div>
      </div>
    </div>

```

## Code Snippets
```css
:root {
  --round: 50%;
  --body-color: #ffc0cb;
  --border-value: 5px solid black;
  --ear-size: 50px;
  --eye-size: 50px;
  --eye-border: 2px solid #000;
  --pupil-size: 50%;
  --nose-width: 100px;
  --nose-height: 60px;
}

.head {
  width: 200px;
  height: 200px;
  background: var(--body-color);
  position: relative;
  border-radius: var(--round);
  border: var(--border-value);
  margin-top: 20px;
}

.ear {
  position: absolute;
  width: var(--ear-size);
  height: var(--ear-size);
  background: var(--body-color);
  border: 5px solid white;
  z-index: -1;
  border-radius: var(--round);
  border: var(--border-value);
  top: -10px;
}

.ear:first-child {
  left: 10px;
}

.ear:nth-child(2) {
  right: 10px;
}

.eye {
  position: absolute;
  top: 40px;
  width: var(--eye-size);
  height: var(--eye-size);
  background: #fff;
  border-radius: var(--round);
  border: var(--eye-border);

  display: flex;
  justify-content: center;
  align-items: center;
}

.eye:first-child {
  left: 30px;
}

.eye:last-child {
  right: 30px;
}

.pupil {
  height: var(--pupil-size);
  width: var(--pupil-size);
  background: #000;
  border-radius: var(--round);
}

.nose {
  position: absolute;
  width: var(--nose-width);
  height: var(--nose-height);
  border-radius: 35%;
  background: #f57187;
  bottom: 30px;
  border: 2px solid #000;
  left: 50%;
  transform: translateX(-50%);

  /* nostril */
  display: flex;
  justify-content: space-around;
  align-items: center;
}

.nostril {
  height: 50%;
  width: 25%;
  border-radius: var(--round);
  background: #000;
}


```
