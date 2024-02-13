# Robot Emoji

<center>

![Robot](https://github.com/SanjeebLama/learning-in-public/assets/51410633/d475a121-62d0-42fe-b270-a707afdfde14)

</center>



## What I Learned
- **It was tougher than I thought:** Initially, I underestimated the complexity. Despite having ideas in my head, I discovered that translating those concepts into tangible designs presented unexpected challenges.

  
## HTTML Snippets
```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta http-equiv="X-UA-Compatible" content="IE=edge" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Document</title>
    <link rel="stylesheet" href="robot.css" />
  </head>
  <body>
    <div class="head">
      <div class="light">
        <div class="bulb"></div>
        <div class="stick"></div>
      </div>

      <div class="ears">
        <div class="ear"></div>
        <div class="ear"></div>
      </div>

      <div class="eyes">
        <div class="eye"></div>
        <div class="eye"></div>
      </div>

      <div class="nose"></div>

      <div class="mouth">
        <div class="tooth"></div>
        <div class="tooth"></div>
        <div class="tooth"></div>
        <div class="tooth"></div>
      </div>
    </div>
  </body>
</html>

```

## Code Snippets
```css
:root {
  --width-head: 150px;
  --height-head: 150px;
  --color-light-stick: #808080;
  --color-light-bulb: #ffa500;
  --color-ear: #c90a0a;
  --color-eye: #fff;
  --color-eye-border: #00b3ff;
  --color-nose: #c90a0a;
  --color-mouth: #dedede;
  --color-tooth: #000;
}

.head {
  position: relative;
  width: var(--width-head);
  height: var(--height-head);
  margin: 50px;
  background: #a4d9eb;
  border: 5px solid #9bbcc2;
  border-radius: 20px;
}

.light {
  position: absolute;
  display: flex;
  flex-direction: column;
  align-items: center;
  left: 50%;
  top: -45px;
  transform: translateX(-50%);
}

.stick {
  width: 10px;
  height: 15px;
  background: var(--color-light-stick);
}

.bulb {
  width: 30px;
  height: 30px;
  background: var(--color-light-bulb);
  border-radius: 50%;
  margin-bottom: -5px;
  z-index: 1;
}

.ear {
  position: absolute;
  top: 50%;
  transform: translateY(-50%);
  width: 10px;
  height: 50px;
  background: var(--color-ear);
}

.ear:first-of-type {
  left: -15px;
  border-top-left-radius: 5px;
  border-bottom-left-radius: 5px;
}

.ear:last-of-type {
  right: -15px;
  border-top-right-radius: 5px;
  border-bottom-right-radius: 5px;
}

.eyes {
  gap: 20px;
  padding-top: 25px;
  display: flex;
  justify-content: center;
}

.eye {
  width: 30px;
  height: 30px;
  background: var(--color-eye);
  border-radius: 50%;
  border: 5px solid var(--color-eye-border);
}

.nose {
  width: 0px;
  height: 0px;
  border-bottom: 30px solid var(--color-nose);
  border-right: 15px solid transparent;
  border-left: 15px solid transparent;

  position: absolute;
  left: 50%;
  top: 50%;
  transform: translate(-50%, -50%);
}

.mouth {
  width: 100px;
  height: 25px;
  border: 1px solid black;
  background: var(--color-mouth);
  position: absolute;
  bottom: 25px;
  left: 50%;
  transform: translateX(-50%);

  display: flex;
  justify-content: space-around;
  border-radius: 20px;
  overflow: hidden;
}

.tooth {
  width: 5px;
  height: 100%;
  background: var(--color-tooth);
}

```
