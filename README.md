# CSS properties
### Font size
* absolute - px
* relative - em, percentages - used when making responsive design

```css
.container {
  font-size: 12px;
}
article {
  font-size: 14px;
}
article h2 {
  font-size: 2em; /* inherit font size from article and miltiple it by 2 */
}
article p {
  font-size: 50%; /* inherit font size from article and take 50% of size */
}
```

### Font family
Note: some families already exist on user's computer. Remember to use the font family stack for fallbacks.
```css
.container {
  font-family: arial, helvetica, sans-serif; /* if arial is not available, use helvetica etc. */
}
```

### Text decoration
Possible values: ```inerhit|line-through|none|underline|overline|inherit```
```css
.container {
  text-decoration: underline;
}
```

### Font weight
Possible values: ```normal|bold|bolder|lighter|number|initial|inherit```

Note: Bold is same as 700, normal is same as 400. Most font families won't have every possible number value.

Note: some font families don't have certain weights as their options!
```css
.container {
  font-weight: bolder;
}
```

### Text color
Changing the color of the text.
```css
 .container {
  color: blue;
  color: #FEFEFE;
 }
```

### Letter spacing and word spacing
Spacing between letters: e.g. s p a c i n g

Spacing between words: e.g. space   between   words

Values mostly in pixels;
```css
.container {
  letter-spacing: 3px;
  word-spacing: 5px;
  letter-spacing: 2em; /* the case with em's is font-size times number of em's */
}
```
### Border style
Mostly used values: solid|none|hidden
```css
.container {
  border: 1px solid black; /* width, style, color */
  border-radius: 10px; /* for rounded corners; it has 4 corners */
  border-radius: 5px 10px 30px 20px; /* different corenrs */
}
```

### Width and height
They Can be static (in pixels) and dynamic (in percentages).
```css
.container {
  height: 100px; /* static height */
  width: 300px; /* static width, no matter how big the browser is */
  width: 70%; /* dynamic, width is 70% of the parent element */
}
.container{
  width: 40%;
  display: inline-block; /* display inline but keep respecting the box model (block elements) */
}
```

### Background
It can be colored or used an image background.
```css
.container {
  width: 500px;
  height: 500px;
  background-color: #606060;
  background-image: url(https:url);
  background-repeat: no-repeat; /* if the image is smaller than the container and we don't want it to repeat */
  background-position: center; /* or we can specify in pixels */
  background-size: 100px; /* if we have an background image, we can resize it */
}
```

# CSS positioning

### Floating elements
Possible values: left|right|inherit|none

Important: removes the element from the real document flow and floats it somewhere.

Example: floating columns
```css
/* both are block level elements */
.left, .right {
  float: left;
  width: 46%; /* not 50% because of padding + margin */
  padding: 1%;. Often used in combination with relative positioning. 
  margin 1%;
  background: yellow;
}
/*
wrapper of .left and .right (always the parent element!)
this css makes sure that anything after the .columns is cleared, meaning, it respects the normal document flow again
(because float will break it)
*/
.columns {
  display: block;
  content: "";
  clear: both;
}
```

### Position
Possible values: static|relative|absolute|fixed|inherit

* relative - the element is positioned relative to its normal position. It does NOT remove content from the normal document flow, it is still occuping it's expected position, but it's mostly just "offseted" from it's original position with top|bottom|right|left (without them nothing will happen). When relative element move, no other element on the layout are affected.
* absolute - allows you to place your element precisely where you want it. Often used in combination with relative positioning. The positioning is done relative to the first relatively (or absolutely) positioned parent element. The element is removed from the normal document flow.
* fixed - mostly used to fix the nav bar to the top, so when we scroll down, it stays "sticky". It also removes the element from the normal document flow.

### Stack order and z-index
Stack order - the further down in the HTML you are, the higher the stacking order is (LIFO).

E.g. for semantic rasons, the navigation should be at the top od the page, but visualy above all elements.

With it```z-index```, we are controling the stacking order.
```css
.nav {
  z-index: 1;
  position: relative; /*when using z-index, we have to include the position value*/
}
```

# Flexbox
A parent element gets a ```display: flex``` property, and his direct desendants become flex items. We can control how they shrink and how they grow. Flex items stack left to right.
Playground: https://codepen.io/collection/AWOkYM/
```css
.container {
  display: flex;
}
```

### flex-grow
If there is room left in the container, items will grow and fill that space.
```css
.box {
  flex-grow: 1; /* grow rate. every box will have the same rate */
}
```

### flex-shrink
Same as ```flex-grow```, just for shrinking items. When we start shrinking the browser window beneath the parent width, the items will shrink in the given rate.

### flex-wrap
If flex-items have a min width, when shrinking the browser, the last element will eventually exit the screen and a scrollbar will appear. If we want to move that item to the next row, we can use ```flex-wrap: wrap```. If we want that item to move above other flex items, we can use ```flex-wrap: wrap-reverse```. Check the codepen url.

### flex-basis
Similar to ```min-width``` but instead of showing the scrollbar when shrinked beneath the defined value, they will shrink as normal flex items.

### justify-content
Aligns the flexible container's items when the items do not use all available space on the main-axis (horizontally).

In other hand, on the cross-axis, the same thing does the ```align-items``` property.

__Important!__ The elements __always__ follow the direction of the main-axis!

Possible values: flex-start|flex-end|center|space-between|space-around|initial|inherit

### flex-flow
Make the flexible items display in reverse order, or vertically.

```css
.container {
  display: -webkit-flex; /* Safari */
  -webkit-flex-flow: row-reverse wrap; /* Safari 6.1+ */
  display: flex;
  flex-flow: row-reverse wrap;
}
```
