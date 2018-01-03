https://jasenpan1987.github.io/trillo/

# Some Notes

## Flex box
1. Flex container (display: flex)
2. Flex items: everything inside flex container
3. Main axis (horizontal default)
4. Cross axis (vertical default)

## Flex properties

### Flex Container
1. flex-direction: row | row-reverse | column | column-reverse
2. flex-wrap: nowrap | wrap | wrap-reverse
3. justify-content: flex-start | flex-end | center | space-between | space-around | space-evenly
4. Align-items: stretch | flex-start | flex-end | center | baseline
5. align-content: stretch | flex-start | flex-end | center | space-between | space-around

### Quick demo
https://codepen.io/anon/pen/eyBQPX?editors=1100

### Flex Item
1. align-self: auto | stretch | flex-start | flex-end | center | baseline
2. order: 0 | any integer
3. flex-grow: 0 | any integer
4. flex-shrink: 1 | any integer
5. flex-basis: auto | any integer
6. flex: 0 1 auto …
### Quick demo
https://codepen.io/anon/pen/aEBQrz?editors=1100

## Css custom properties (aka css variables)
Define properties:
```
:root { 
  --color-primary: #eb2f64;
  --color-primary-light: #FF3366;
  --color-primary-dark: #BA265D;
  …
}
```
the custom properties only available to its parent or current scope, so we need to use the :root pesudo element to make the properties available everywhere.

To use the properties, we can simply use var(--varname)
Such as background-color: var(--color-primary);

## svg
Why svg over icon font:
Screen-readers fail to read icon fonts

https://icomoon.io/

```
<svg class="search__icon">
  <use xlink:href="img/sprite.svg#icon-magnifying-glass">
  </use>
</svg>
```
Have to use a web server and can be styled in css.
To set the height and width of an svg element, we can simply use the height and width.

fill: currentColor;
This means the svg follows its parent’s color. It also works on hover, visited… just like inherit colored.

## How to vertically align items
```
.parent {
	display: flex;
	flex-direction: column; // now the y axis become to the main axis
	justify-content: space-between; 
}
```

## How to center two sibling elements
```
.parent {
  display: flex;
  align-item: center;
}
```
Z-index only work on elements have position specified.

In flex box, we can use margin-xxx: auto to get the same result as flex: 1, but only occupies the space it need, the remaining space will become the margin of the element.

### Quick demo https://codepen.io/anon/pen/MrJzWv

## How to make modular button
```
.btn-inline {
  border: none;
  color: var(--color-primary);
  font-size: inherit; // 1)
  border-bottom: 1px solid currentColor; // 2)
  padding-bottom: 2px;
  display: inline-block;
  background-color: transparent; // 3)
  cursor: pointer;
  transition: .3s;

  &:hover {
    color: var(--color-grey-dark-1);
  }
}
```
1) we set it to inherit, so it can inherit the font-size from its parent, more flexable.

2) we set the border color to currentColor, which means the current color of THIS element, so if we want to change its color when hover, we don’t have to specify it again.

3) we don’t have to set the color to the same color as its parent.


## Animation
In css, animation can be set to infinite, first set the keyframe, then add the infinite to the element apply it.

```
&:focus { // clicked
    outline: none;
    animation: pulse 1s infinite;
  }

@keyframes pulse {
  0% {
    transform: scale(1);
    box-shadow: none;
  }

  50% {
    transform: scale(1.05);
    box-shadow: 0 1rem 4rem rgba(0, 0, 0, .25);
  }

  100% {
    transform: scale(1);
    box-shadow: none;
  }
}
```
### align-item default is stretch 

### Magical button:
https://codepen.io/anon/pen/LexaeK?editors=1100

###Css variables don’t work with media queries
