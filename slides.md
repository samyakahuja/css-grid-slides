---
theme: seriph
class: "text-center"
highlighter: shiki
lineNumbers: false
background: https://source.unsplash.com/Vwf8q3RzBRE/1920x1279
---

# CSS Grids

<div class="abs-br m-6 flex gap-2">
  <a href="https://github.com/samyakahuja/css-grid-slides" target="_blank" alt="GitHub"
    class="text-xl icon-btn !border-none !hover:text-white">
    <carbon-logo-github />
  </a>
</div>

---

# Browser Support

- according to [caniuse](https://caniuse.com/css-grid) **95%** of tracked
  desktop traffic uses a browser that supports css grids.
- IE 11 also supports css grids, but an older verson of the spec. For seeing
  what differences are there, there's a great article from
  [css-tricks](https://css-tricks.com/css-grid-in-ie-debunking-common-ie-grid-misconceptions/)
- if you are not sure, then provide a base style, and then add additional css
  for browsers that support css grids

  ```css
  .wrapper {
    display: flex;
  }

  @supports (display: grid) {
    .wrapper {
      display: grid;
    }
  }
  ```

  <span class="text-sm opacity-50">
    Note: IE 11 does not support `@supports` keyword, hence the styles
    inside it are automatically ignored.
  </span>

---
layout: two-cols
---

# Grid Terminology

- **grid lines**: grid is made up of lines that run horizontally and vertically,
they are numbered from 1 and follow the writing mode. 
- **grid tracks**: space between two grid lines
- **grid cell**
- **grid area**: several grid cells together, created by causing an item to span
over multiple tracks.
- **grid-gap**: spacing between tracks. grid items can span across them.

The rows are always arranged along the "block" axis. Columns are always arranged along the "inline" axis.

::right::

inspect the grid using browser dev-tools

<div class="wrapper">
  <div class="box"></div>
  <div class="box"></div>
  <div class="box"></div>
  <div class="box"></div>
  <div class="box"></div>
</div>

<style>
.wrapper {
  display: grid;
  grid-template-columns: repeat(3, 100px);
  grid-template-rows: repeat(2, 100px);
  gap: 16px;
}

.box {
  background-color: pink;
}

.grid-cols-2 {
  gap: 32px;
}
</style>

---
layout: center
class: "text-center"
---

# Tenets of css grids

Rules to keep in mind before delving into the details

---
layout: center
class: "text-center"
---

- All the cells in a column should have equal width.

<figure>
<img src="https://css-grid-gules.vercel.app/grids/same-column-width.svg">
<figcaption class="text-sm opacity-70 mt-2">This is a valid grid where all the cells in the column are 250px
</figcaption>
</figure>


<style>
  * {
    box-sizing: border-box;
  }

  figure {
    width: min-content;
    padding: 16px;
    margin: 0 auto;
  }

  figure img {
    width: 250px;
    max-width: revert;
  }
</style>

---
layout: center
class: "text-center"
---

- All the cells in a row should have equal height.

<figure>
<img src="https://css-grid-gules.vercel.app/grids/same-row-height.svg">
<figcaption class="text-sm opacity-70 mt-2">This is a valid grid where all the cells in a row are equal height (even though all the rows are of different height)</figcaption>
</figure>


<style>
  * {
    box-sizing: border-box;
  }

  figure {
    width: min-content;
    padding: 16px;
    margin: 0 auto;
  }

  figure img {
    width: 250px;
    max-width: revert;
  }
</style>

---
layout: center
class: "text-center"
---

- Each column needs to have same number of rows (cells).
- Each row needs to have same number of columns (cells).

<figure>
<img src="https://css-grid-gules.vercel.app/grids/unequal-row-column.svg">
<figcaption class="text-sm opacity-70 mt-2">This in a invalid grid since the first row has 1 column and second row has 2 columns.</figcaption>
</figure>

<style>
  * {
    box-sizing: border-box;
  }

  figure {
    width: min-content;
    padding: 16px;
    margin: 0 auto;
  }

  figure img {
    width: 250px;
    max-width: revert;
  }
</style>

---
layout: two-cols
---

# Holup

If the previous grid was invalid, then how do we create the *holy grail* layout with grids?

<figure>
<img src="https://css-grid-gules.vercel.app/grids/holy-grail.svg">
<figcaption class="text-sm opacity-70 mt-2">Holy grail layout</figcaption>
</figure>

::right::

<v-click>

Well we do it with overlapping grid items.

<figure>
<img src="https://css-grid-gules.vercel.app/grids/holy-grail-grid.svg">
<figcaption class="text-sm opacity-70 mt-2">Holy grail layout where grid items span multiple cells</figcaption>
</figure>

</v-click>

<style>
  * {
    box-sizing: border-box;
  }

  figure {
    width: min-content;
    padding: 16px;
    margin: 0 auto;
  }

  figure img {
    width: 250px;
    max-width: revert;
  }

.grid-cols-2 {
  gap: 32px;
}

.col-right p {
  text-align: center;
  margin-top: 50px;
  opacity: 0.7;
}
</style>

---

# Takeaways

<br>

<p class="text-center ">
With CSS Grid the structure happens exclusively in CSS. There are no DOM nodes
that represent the rows or columns in CSS Grid. Instead, the rows and columns
are invisible markers, tools that our HTML elements can use to position
themselves.
</p>

<br>

<p class="text-center">
Rows and columns are like the lines painted on the ground in parking lots.
Drivers can use these lines to align their vehicles, but really they're just
symbols. It's up to the driver to decide how to use them.
</p>

---
layout: center
class: "text-center"
---

# Let's play a game

<a class="rocket-link" href="https://css-grid-gules.vercel.app/is-grid-valid" target="_">
<uim-rocket class="text-3xl text-orange-400 animate-pulse animate-faster" />
</a>

<style>
.rocket-link {
  border: none;
  border-style: none;
  outline: none;
}

.rocket-link:hover {
  border: none;
}

.rocket-link:hover svg {
  color: green;
  animation: unset;
}
</style>


---

# Show me the code!

```css
display: grid;
gap: 16px;
```

<br>

<div class="wrapper">
<div class="box">1</div>
<div class="box">2</div>
<div class="box">3</div>
<div class="box">4</div>
</div>

<div class="opacity-50 text-sm abs-br m-6 mb-7 flex gap-2">
try changing <code>grid-auto-flow</code> to <code>column</code> (grid auto flow values relate to relate to the writing mode of the document).
</div>
<div class="opacity-50 text-sm abs-br mb-2 mr-6 flex gap-2">
also try giving each box a margin of top and bottom, why is there no margin collapse?
</div>

<style>
.wrapper {
  display: grid;
  gap: 16px;
  grid-auto-flow: unset;
}

.box {
  padding: 16px;
  background: peachpuff;
}
</style>

---

# 1fr and minmax

```css
display: flex;
```

<div class="wrapper wrapper-flex">
  <div class="box">hello</div>
  <div class="box">I'm</div>
  <div class="box">A really long sentence</div>
</div>

```css
grid-template-columns: repeat(3, auto);
```

<div class="wrapper wrapper-auto">
  <div class="box">hello</div>
  <div class="box">I'm</div>
  <div class="box">A really long sentence</div>
</div>

```css
grid-template-columns: repeat(3, 1fr); /* 1fr = minmax(auto, 1fr) */
```

<div class="wrapper wrapper-1fr">
  <div class="box">hello</div>
  <!-- <div class="box">I'm</div> -->
  <div class="box">A really long sentence</div>
  <div class="box"></div>
</div>

```css
grid-template-columns: repeat(3, minmax(0, 1fr));
```

<div class="wrapper wrapper-minmax">
  <div class="box">hello</div>
  <!-- <div class="box">I'm</div> -->
  <div class="box">A really long sentence</div>
  <div class="box"></div>
</div>

<div class="opacity-50 text-sm abs-br m-6 flex gap-2">
note: try adjusting the width of the grids and see what happens
</div>

<style>
.wrapper {
  display: grid;
  gap: 8px;
  width: 300px;
  margin: 8px auto;
}

.box {
  background-color: pink;
}

.wrapper-flex {
  display: flex;
}

.wrapper-auto {
  grid-template-columns: repeat(3, auto);
}

.wrapper-1fr {
  grid-template-columns: repeat(3, minmax(auto, 1fr));
}

.wrapper-minmax {
  grid-template-columns: repeat(3, minmax(0, 1fr));
}

.shiki-container {
  width: fit-content;
  margin: 0 auto;
  margin-top: 16px;
}

.slidev-layout {
  padding: 0;
}

h1 {
  padding-top: 10px;
  text-align: center;
}
</style>
---

`fr` is a flexible length (not static, like `px`, `em`, `%`) which
describes a share of the available space in the grid container. It distributes
space after the items have been laid out. 

<hr>

Grids have a function called `minmax` that allows us to set a minimum and a
maximum size for a track.

`fr` can actually be written as `minmax(auto, fr)`. Grid looks at the intrinsic
size of the content, then distributes available space after giving the content
enough room. This means that you might not get tracks that each have an equal
share of all space available in the grid container.

<hr>

To force a track to take an equal share of the space in the grid container minus
gaps use minmax. Replace `1fr` as a track size with `minmax(0, 1fr)`. This makes the
minimum size of the track 0 and not the min-content size.

<hr>

**Quick gotcha**: the flexible unit has to come last. `minmax(1fr, 250px)` is
invalid, because `1fr` isn't a valid "minimum" value.

---

# Generating columns with auto-fill (and auto-fit)

`repeat` accepts *special keywords* in addition to numbers

<br>

<Footer />

<v-click>

<br>

This is the fundamental difference between auto-fill (lots of empty columns) and auto-fit (stretched ultra-wide columns).

</v-click>

---

# [justify-content](https://developer.mozilla.org/en-US/docs/Web/CSS/justify-content)

distribute additional space in the grid container around or between **columns** (inline axis).

The default behaviour in CSS Grid is to stretch the columns to take up all available space.

<div class="jc-wrapper">
  <div class="jc-grid">
    <div>Hello World</div>
    <div>Stuff here</div>
    <div>Some long content</div>
  </div>
</div>

If we give it an explicit width

<div class="jc-wrapper">
  <div class="jc-grid jc-grid-fixed-width">
    <div>Hello World</div>
    <div>Stuff here</div>
    <div>Some long content</div>
  </div>
</div>

There are some properties that make sense when we have multiple columns:

<div class="jc-wrapper">
  <div class="jc-grid jc-grid-2-cols">
    <div>Hello World</div>
    <div>Stuff here</div>
    <div>Some long content</div>
    <div>other content</div>
  </div>
</div>

<style>
  .jc-wrapper {
    width: 400px;
    padding: 8px;
    border: 1px solid gray;
  }

  .jc-grid {
    display: grid;
  }

  .jc-grid * {
    outline: 1px solid black;
  }

  .jc-grid-fixed-width {
    grid-template-columns: 200px;
  }

  .jc-grid-2-cols {
    grid-template-columns: auto auto;
    justify-content: space-between
  }
</style>

---

# [justify-items](https://developer.mozilla.org/en-US/docs/Web/CSS/justify-items)

set `justify-self` property to align items inside grid on inline axis

uses `justify-content: center`

<div class="jc-wrapper">
  <div class="jc-grid">
    <div>Hello World</div>
    <div>Stuff here</div>
    <div>Some long content</div>
  </div>
</div>

<br>

uses `justify-items: center`

<div class="ji-wrapper">
  <div class="ji-grid">
    <div>Hello World</div>
    <div>Stuff here</div>
    <div>Some long content</div>
  </div>
</div>

<v-click>

At first glance, this seems to violate one of our core principles: columns
aren't supposed to change their width across different rows!

Upon closer inspection, though, we notice something interesting. The columns are
actually full-width! But the items within the column have been shrunk down and
centered.

</v-click>

<style>
  .jc-wrapper, .ji-wrapper {
    width: 400px;
    padding: 8px;
    border: 1px solid gray;
  }

  .jc-grid, .ji-grid {
    display: grid;
  }

  .jc-grid *, .ji-grid * {
    outline: 1px solid black;
  }

  .jc-grid {
    justify-content: center;
  }

  .ji-grid {
    justify-items: center;
  }
</style>

---

# Alignment

So in a nutshell

In grid the properties which begin with `justify-` are always used on the inline
axis. And the properties which begin with `align-` are used on the block axis.

- [justify-content](https://developer.mozilla.org/docs/Web/CSS/justify-content)
and [align-content](https://developer.mozilla.org/docs/Web/CSS/align-content):
distribute additional space in the grid container around or between tracks.
- [justify-self](https://developer.mozilla.org/docs/Web/CSS/justify-self) and
[align-self](https://developer.mozilla.org/docs/Web/CSS/align-self): are applied
to a grid item to move it around inside the grid area it is placed in.
- [justify-items](https://developer.mozilla.org/docs/Web/CSS/justify-items) and
[align-items](https://developer.mozilla.org/docs/Web/CSS/align-items): are
applied to the grid container to set all of the justify-self properties on the
items.

---

# Placing Items

- header has height of 30px and footer of 50px
- nav has width of 80px and aside of 50px
- main should fill the available space

<br>

<div class="two-col">

<div class="pi-wrapper pi-wrapper-sol">
  <header></header>
  <nav></nav>
  <main></main>
  <aside></aside>
  <footer></footer>
</div>

<div class="pi-wrapper">
  <header></header>
  <nav></nav>
  <main></main>
  <aside></aside>
  <footer></footer>
</div>

</div>

<style>
.two-col {
  height: 300px;
  display: grid;
  grid-template-columns: 1fr 1fr;
  grid-gap: 16px;
}

.pi-wrapper {
  min-height: 100%;
  display: grid;
  outline: 1px solid black;
}

.pi-wrapper header {
  background: yellow;
}

.pi-wrapper nav {
  background: green;
}

.pi-wrapper main {
  background: blue;
}

.pi-wrapper aside {
  background: pink;
}

.pi-wrapper footer {
  background: red;
}

.pi-wrapper * {
  opacity: 0.4;
}

.pi-wrapper-sol {
  grid-template-columns: 80px 1fr 50px;
  grid-template-rows: 30px 1fr 50px;
  grid-template-areas:
    "header header header"
    "nav main aside"
    "footer footer footer"
  ;
}

.pi-wrapper-sol header {
  grid-area: header;
}

.pi-wrapper-sol nav {
  grid-area: nav;
}

.pi-wrapper-sol main {
  grid-area: main;
}

.pi-wrapper-sol aside {
  grid-area: aside;
}

.pi-wrapper-sol footer {
  grid-area: footer;
}
</style>

---

# Tools for placement

There are a plethora of properties, but here are the important ones 

The properties that you can use to place items by line number are:

- [grid-column](https://developer.mozilla.org/docs/Web/CSS/grid-column)
- [grid-row](https://developer.mozilla.org/docs/Web/CSS/grid-row)

they set the start and end lines of the grid area that the item should be placed into.

<hr>

You can also name areas of the grid and place items onto those named areas.

- Use [grid-area](https://developer.mozilla.org/docs/Web/CSS/grid-area) to give any item in the grid a name.
- Use [grid-template-areas](https://developer.mozilla.org/docs/Web/CSS/grid-template-areas) to define which grid cells each item will span

---

# Learn More

- [Reconsider the meaning of 1fr](https://github.com/w3c/csswg-drafts/issues/1777)
- [A Deep Dive Into CSS Grid minmax()](https://ishadeed.com/article/css-grid-minmax/)
- [Full-Bleed Layout Using CSS Grid](https://www.joshwcomeau.com/css/full-bleed/)
- [Preventing overflow when using CSS Grid](https://css-tricks.com/preventing-a-grid-blowout/)
- [Position sticky with CSS Grid](https://ishadeed.com/article/position-sticky-css-grid/)