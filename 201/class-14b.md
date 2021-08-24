# CSS Transforms, Transitions, and Animations
## Transforms
- The transform property comes in two different settings, two-dimensional and three-dimensional. Each of these come with their own individual properties and values.  

**Syntax**: 
```
div {
  -webkit-transform: scale(1.5);
     -moz-transform: scale(1.5);
       -o-transform: scale(1.5);
          transform: scale(1.5);
}

```

### 2D Transforms
- you can rotate an element with `transform: rotate(## deg)` property.

- Also, you can rotate an element along any axis by `transform: rotateX(## deg)`(for X-axis) `transform: rotateY(## deg)` (for Y-axis)

- You can make an figure appear bigger or smaller by the `transform: scale(##);` property

- Also, you scale with respect to axis by `transform: scaleX(.5);`(for X-axis) or `transform: scale(.5, 1.15);` (X & Y axises)

- you can position an element  without interrupting its normal flow, just like `relative position` with `transform: translateX(-10px);` (X-axis) and `transform: translateY(25%);` for (Y-axis) or both.

- You distort an element along an axis with ` transform: skewX(5deg);` (for X-axis) `transform: skewY(-20deg);` (for Y-axis)

- You can combine between to properties of transform ; `transform: rotate(25deg) scale(.75);`

- The default transform origin is the dead center of an element, both 50% horizontally and 50% vertically. To change the origin use the `transform-origin` property. ;`transform-origin: 0 0;` or ` transform-origin: 100% 100%;` or `transform-origin: top left;`

- The perspective of an element can be set in two different ways. One way includes using the `perspective` value within the transform property on individual elements, while the other includes using the `perspective` property on the parent element residing over child elements being transformed.
    - ( individual perspectives with the perspective value) `transform: perspective(200px) rotateX(45deg);`
    - ( perspective property on their direct parent element.) `perspective: 200px;`

- You can also set a perspective-origin just like transform-origin with `perspective-origin: 0 0;`

### 3D Transforms
- You can change elements on the z axis.

- you can use both `scale` and `rotate` properties along the Z-axis

- Elements may also be translated on the Z-axis using the `translateZ` value. A negative value here will push an element further away on the z axis, resulting in a smaller element. Using a positive value will pull an element closer on the Z-axis, resulting in a larger element.

- Use `backface-visibility` and set its value to `hidden` to hide elements that are back faced.

## Transitions & Animations
With `CSS`3 transitions you have the potential to alter the appearance and behavior of an element whenever a state change occurs, such as when it is hovered over, focused on, active, or targeted.

Animations within `CSS`3 allow the appearance and behavior of an element to be altered in multiple keyframes. Transitions provide a change from one state to another, while animations can set multiple points of transition upon different keyframes.

### Transition
- The easiest way for determining styles for different states is by using the `:hover`, `:focus`, `:active`, and `:target` pseudo-classes.

- There are four transition related properties in total, including `transition-property`, `transition-duration`, `transition-timing-function`, and `transition-delay`

- you can alter more than one property when doing transitions: `transition-property: background, border-radius;` 
```
.box:hover {
    background: #ff7b29;
    border-radius: 50%;
  }

```

- The duration in which a transition takes place is set using the `transition-duration`

- The `transition-timing-function` property is used to set the speed in which a transition will move.

- The `linear` keyword value identifies a transition moving in a constant speed from one state to another.

- The `ease-in` value identifies a transition that starts slowly and speeds up throughout the transition.

- The `ease-out` value identifies a transition that starts quickly and slows down throughout the transition.

- The `ease-in-out` value identifies a transition that starts slowly, speeds up in the middle, then slows down again before ending.

- You can also set a delay with the `transition-delay` property 

- You can shorthand transitions like this: `transition: background .2s linear, border-radius 1s ease-in 1s;`

### Animations
- To set multiple points at which an element should undergo a transition, use the `@keyframes` rule. The `@keyframes` rule includes the animation name, any animation breakpoints, and the properties intended to be animated.
```
@keyframes slide {
  0% {
    left: 0;
    top: 0;
  }
  50% {
    left: 244px;
    top: 100px;
  }
  100% {
    left: 488px;
    top: 0;
  }
}

```


- Use `animation-name` after declaring keyframes for an animation with the animation name as the property value
```
.stage:hover .ball {
  animation-name: slide;
}

```

- You also can/need to identify `animation-duration`, `animation-timing-function` and `animation-delay` to make youe animation more linear.

- Animations also provide the ability to further customize an element’s behavior, including the ability to declare the number of times an animation runs, as well as the direction in which an animation completes.

- You can define how many times the animation will run by `animation-iteration-count` property

- You can also declare the direction an animation completes using the `animation-direction` property. Values for the `animation-direction` property include `normal`, `reverse`, `alternate`, and `alternate-reverse`.

- `animation-play-state` property allows an animation to be played or paused using the `running` and `paused` keyword values respectively. Like deciding if the animation will be running from the start of until clicking or hovering

- The `animation-fill-mode` property identifies how an element should be styled either before, after, or before and after an animation is run. The animation-fill-mode property accepts four keyword values, including `none`, `forwards`, `backwards`, and `both`



# References:  

- [Transforms](https://learn.shayhowe.com/advanced-html-css/css-transforms/)

- [Transitions & Animations](https://learn.shayhowe.com/advanced-html-css/transitions-animations/)