# Tween

- "tween" refers to a type of animation that transitions an object or element between two states over a specified duration.
- "Tween" is short for "in-between", indicating that the animation creates the illusion of continuous motion between the starting and ending states.

> Imagine you have a toy car. When you push it gently, it moves slowly, and when you push it hard, it moves quickly. Tweens are like telling the toy car how to move from one place to another in a smooth and nice way, like when you gently push it to make it move smoothly. It's like giving the toy car instructions to move smoothly between two points!

- you can tween properties like position, size, color, opacity, and more.

## Common methods for creating a Tween:

gsap.to()
gsap.from()
gsap.fromTo()

#### `gsap.to()`:

- This is a function in GSAP that creates a tween to animate one or more properties of an object or element from their current values to specified end values.

- GSAP figures out the current values automatically (you don't need to define starting values, though you can in a `fromTo()` tween)

**Syntax:**
`gsap.to(target, vars);`

`gsap.to(target, { duration: value, options });`

- **target:** This is the element or object that you want to animate. It can be specified using a _CSS selector (like ".box" GSAP uses document.querySelectorAll() internally), an HTML element (like document.getElementById("box")), or a JavaScript object._

- **vars:** an object containing all the properties/values you want to animate, along with any special properties like ease, duration, delay, or onComplete (listed below). https://gsap.com/docs/v3/GSAP/gsap.to()#special-properties

  - **duration:** This is the duration of the animation in **seconds**. It specifies how long the animation will take to complete. _Default Duration of 0.5 i.e 500 miliseconds_

  - **options:** These are the properties and values that define how the animation should behave. They include things like the properties you want to animate (like x, y, opacity, etc.), the end values of those properties, easing functions, delays, and callbacks. Options are specified using key-value pairs within an object.

Example:

`gsap.to(".box", { duration: 1, x: 100 });`

```js
gsap.to(".box", {
  x: 600, //translateX
  y: 400, //translateY
  scale: 3,
  rotation: 360,
  duration: 3,
});
```

> GSAP updates the inline styles. Behind the scenes gsap changes the target’s inline style during the animation.

###### **Good to know:**

- [Function-based values](<https://gsap.com/docs/v3/GSAP/gsap.to()#function-based-values>)

```js

gsap.to(".class", {
x: 100, //normal value
y: function(index, target, targets) { //function-based value
return index \* 50;
},
duration: 1
});

```

- [Random values](<https://gsap.com/docs/v3/GSAP/gsap.to()#random-values>)

```js
gsap.to(".class", {
  // chooses a random number between -100 and 100
  // for each target, rounding to the closest 5!
  x: "random(-100, 100, 5)",
});

gsap.to(".class", {
  x: "random([0, 100, 200, 500])", // randomly selects one of the values (0, 100, 200, or 500)
});
```

- Relative values: Use a"+=" or "-=" prefix to indicate a relative value. For example, gsap.to(".class", {x:"-=20"}); will animate x 20 pixels less than whatever it is when the tween starts. {x:"+=20"} would add 20. To use a variable in a relative way, simply add the "+=" or "-=" prefix, like {x: "+=" + yourVariable}.

- Staggers: If multiple targets are defined, you can easily stagger (offset) the start times for each by setting a value like stagger: 0.1 (for 0.1 seconds between each start time).Or you can get much more advanced staggers by using a stagger object

- Sequencing

- Keyframes: If you find yourself animating the same target over and over again, you should definitely check out Keyframes which can make your code much more concise.

#### `gsap.from()`:

- animates from Custom state to the objects natural state
- The from method is used in GSAP to create a tween where you specify the starting values of the properties you want to animate.
- Think of a gsap.from() like a _backwards tween where you define where the values should START, and then it animates to the current state_ which is perfect for animating objects onto the screen because you can set them up the way you want them to look at the end and then animate in from elsewhere

```js
gsap.from(".box", {
  x: 600, //translateX
  y: 400, //translateY
  scale: 3,
  rotation: 360,
  duration: 3,
});
```

> > > However, from tweens can be a little tricky. One of the [most common GSAP mistakes](https://gsap.com/resources/mistakes/) is misusing them. Make sure to use them responsibly!

#### `gsap.fromTo()`:

- This method in GSAP combines the functionality of both from and to. It allows you to specify both the starting values and the ending values for the properties you want to animate.
- This tween lets you **define BOTH the starting and ending values** for an animation (as opposed to `from()` and `to()` tweens which use the current state as either the start or end).
- This is great for having full control over an animation, especially when it is chained with other animations

**Syntax:**
`gsap.to(target, fromVars, toVars);`

- FromVars = starting state

```js
gsap.fromTo(".box", { opacity: 0 }, { opacity: 0.5, duration: 1 });
```

```js
let tween = gsap.fromTo(
  ".class",
  { opacity: 0 },
  { opacity: 0.8, duration: 1, ease: "elastic" }
);
tween.pause();
tween.seek(2);
tween.progress(0.5);
tween.play();
```

In simpler terms, `gsap.to()` makes things change from their current state to a new state, `gsap.from()` makes things start from a certain state and change to it's natural state, and `gsap.fromTo()` lets you say exactly where things should start and end up.

### For best performance animate CSS Transform values and opacity

- x
- y
- rotation
- rotationX
- rotationY
- skewX and skewY
- scaleX, scaleY, or just scale

### GSAP can animate any numeric property

- width and height
- backgroundColor \*hyphenated values need to be camelCase
- color
- padding
- left and top _(must set position to relative, absolute, or fixed)_
- vh and vw

> Changing values that are not CSS Transforms or opacity can cause the browser to re-do its layout of the page which in extreme situations can hinder performance.

### gsap.defaults()

https://gsap.com/docs/v3/GSAP/gsap.defaults()/

if you want to change the default ease and duration of all tweens you'd do:

```js
gsap.defaults({
  ease: "power2.in",
  duration: 1,
});
```

- `gsap.defaults()` lets you set properties that should be inherited by ALL tweens (that dont have `inherit:false` set) unless overridden by that tween.

- General configuration settings that arent Tween-specific (like units, autoSleep, and force3D) should be set using `gsap.config()` instead.

### Special Properties :

some of the special properties that can be used with GSAP animations:

| Property            | Description                                                                                                                                    | Example Values                                                 |
| ------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------- |
| `duration`          | The duration of the animation, specified in seconds.                                                                                           | `1` (1 second) = `1000` (1000 milliseconds)                    |
| `delay`             | The delay before the animation starts, specified in seconds.                                                                                   | `0.5` (0.5 seconds) =`500` (500 milliseconds)                  |
| `ease`              | The easing function applied to the animation, controlling the acceleration and deceleration of the motion.                                     | `"power2.inOut"`, `"elastic.out(1, 0.3)"`                      |
| `repeat`            | The number of times the animation should repeat.                                                                                               | `2` (repeats twice), `Infinity` or `-1` (repeats indefinitely) |
| `yoyo`              | Whether the animation should alternate direction on each repeat.                                                                               | `true`, `false`                                                |
| `onStart`           | A callback function to be called when the animation starts.                                                                                    | `() => { console.log("Animation started!") }`                  |
| `onComplete`        | A callback function to be called when the animation completes.                                                                                 | `() => { console.log("Animation completed!") }`                |
| `onUpdate`          | A callback function to be called on each update of the animation's progress.                                                                   | `progress => { console.log("Progress:", progress) }`           |
| `onRepeat`          | A callback function to be called each time the animation repeats.                                                                              | `() => { console.log("Animation repeated!") }`                 |
| `onReverseComplete` | A callback function to be called when the animation completes in reverse mode.                                                                 | `() => { console.log("Reverse animation completed!") }`        |
| `paused`            | Whether the animation should start in a paused state.                                                                                          | `true`, `false`                                                |
| `overwrite`         | Determines how the animation behaves if it overlaps with another animation targeting the same properties.                                      | `"auto"`, `"none"`, `"all"`                                    |
| `autoAlpha`         | Automatically handles opacity and visibility of the element during the animation.                                                              | `0` (completely transparent), `1` (fully visible)              |
| `immediateRender`   | Determines whether the animation should immediately render without delay.                                                                      | `true`, `false`                                                |
| `stagger`           | Adds a [stagger](https://gsap.com/resources/getting-started/Staggers) effect to the animation, applying a delay to each element in a sequence. | `0.2` (0.2 seconds),                                           |

- A stagger object gives you greater control over where the staggers start from and how the timing is dispersed.

```js
gsap.to("#divSection img", {
  y: -50,
  stagger: {
    each: 0.2,
    from: "end",
  },
});
```

- `each:`0.2 means there will be 0.2 seconds _between the start of each animation._

- `amount`:0.2 then all animations will _start within 0.2 seconds._

#### Ease format used in GSAP:

- [Ease Visualizer](https://gsap.com/docs/v3/Eases/)

- Choosing the right ease is one of the most important parts of scripted animation.
  - eases dictate the rate of change of an animation
  - eases dictate the direction of change of an animation (bounce, back, elastic, etc)
  - steep curves cause quick rate of change
  - flat curves cause slow rate of change
  - you can create your own ease curve using Custom Ease.

| Ease Format  | Description                                                                                                                                                      | Example                                                  |
| ------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------- |
| Name         | GSAP provides various predefined easing functions with names that describe their behavior, such as "ease-in", "ease-out", "ease-in-out" , "back", "bounce", etc. | `"power2.inOut"`, `"back.out(1.7)"`                      |
| Cubic Bezier | Custom easing functions defined using cubic Bezier curves, which allows for fine-tuning of acceleration and deceleration.                                        | `[0.42, 0, 0.58, 1]`                                     |
| Steps        | Step-based easing functions that mimic discrete animation steps, useful for creating flipbook-style animations or effects.                                       | `"steps(4, "end")"`, `"steps(10)"`                       |
| Custom       | You can define your own custom easing functions using JavaScript functions or equations.                                                                         | `CustomEase.create("custom", "M0,0 C0.48,0 0.76,1 1,1")` |

> steep curve = quick rate of change
> flat curve = low rate of change

Each of these ease formats provides different ways to control the acceleration and deceleration of animations in GSAP, allowing you to achieve various effects and create animations that suit your design requirements.

Resources [here: GSAP3 Special Eases](https://www.creativecodingclub.com/courses/take/gsap3-special-eases/texts/9490497-slowmo-overview)

[Bookmark](https://www.creativecodingclub.com/courses/take/gsap-3-express/lessons/9341932-reading-ease-curves)

[Tween Control](https://codepen.io/snorkltv/pen/PoojYPV)

Try:

1. https://www.calm.com/schools/resources?day=2

Study the methods and properties of the **GSAP object and Tween class**. I can't stress enough how important this. There is so much good info in the docs.

# Timeline

- A container for multiple tweens and other timelines.
- A timeline is created with gsap.timeline();
- All tweens in a timeline naturally play one after the other.

> A Timeline is a powerful sequencing tool that acts as a container for tweens and other timelines, making it simple to control them as a whole and precisely manage their timing. Without Timelines, building complex sequences would be far more cumbersome because you'd need to use a delay for every animation. For example:

```js
//WITH Timelines (cleaner, more versatile)
var tl = gsap.timeline({ repeat: 2, repeatDelay: 1 });
tl.to("#id", { x: 100, duration: 1 });
tl.to("#id", { y: 50, duration: 1 });
tl.to("#id", { opacity: 0, duration: 1 });

// then we can control the whole thing easily...
tl.pause();
tl.resume();
tl.seek(1.5);
tl.reverse();
```

#### Here's a table summarizing the positioning options for animations in a GSAP timeline:

| Position Parameter | Description                                                                                                              | Example                                     |
| ------------------ | ------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------- |
| Absolute time      | Specifies an absolute time (in seconds) measured from the start of the timeline.                                         | `tl.to(".class", { x: 100 }, 3);`           |
| Label              | Refers to a label defined in the timeline. If the label doesn't exist, it's added to the end of the timeline.            | `tl.to(".class", { x: 100 }, "someLabel");` |
| "<"                | Points to the start of the previous animation, effectively inserting the new animation at the start of the previous one. | `tl.to(".class", { x: 100 }, "<");`         |
| ">"                | Points to the end of the previous animation, effectively inserting the new animation at the end of the previous one.     | `tl.to(".class", { x: 100 }, ">");`         |
| Relative values    | Uses complex strings with "+=" or "-=" prefixes for relative positioning.                                                | `tl.to(".class", { x: 100 }, "<+=2");`      |
| Percentage-based   | Specifies positioning based on a percentage of total animation duration.                                                 | `tl.to(".class", { x: 100 }, "+=50%");`     |

These positioning options allow precise control over where animations are placed within a GSAP timeline, enabling you to create complex sequences and coordinate multiple animations with ease.

> The secret to doing awesome animation in sequencing is the position parameters.

**(Control Panel)[https://codepen.io/snorkltv/pen/oNNwNBr?editors=1000]**

```js
var animation = gsap
  .timeline()
  .from("#demo", { duration: 1, opacity: 0 })
  .from("#title", { opacity: 0, duration: 3, scale: 0, ease: "back" })
  .from(
    "#freds img",
    { y: 160, stagger: 0.5, duration: 0.8, ease: "back" },
    "+=0.5"
  )
  .add("test") // start animation from here
  .from("#time", { xPercent: 100, duration: 1, ease: "bounce" });

document.getElementById("play").onclick = () => animation.play();
document.getElementById("pause").onclick = () => animation.pause();
document.getElementById("reverse").onclick = () => animation.reverse();
document.getElementById("restart").onclick = () => animation.restart();
document.getElementById("test").onclick = () => animation.play("test"); // this is the add("test") control
```

```html
<div>
  <button id="play">play</button>
  <button id="pause">pause</button>
  <button id="reverse">reverse</button>
  <button id="restart">restart</button>
  <button id="test">test</button>
</div>
```
