---
theme: seriph
class: "text-center"
highlighter: shiki
lineNumbers: false
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

Well we do it with overlapping grid items.

<figure>
<img src="https://css-grid-gules.vercel.app/grids/holy-grail-grid.svg">
<figcaption class="text-sm opacity-70 mt-2">Holy grail layout where grid items span multiple cells</figcaption>
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
try changing <code>grid-auto-flow</code> to <code>column</code>
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
grid-template-columns: repeat(3, minmax(auto, 1fr));
```

<div class="wrapper wrapper-1fr">
  <div class="box">hello</div>
  <!-- <div class="box">I'm</div> -->
  <div class="box">A really long sentence</div>
  <div class="box"></div>
</div>

```css
grid-template-columns: repeat(3, minmax(0, 1fr)); /* which is same as repeat(3, 1fr) */
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

This is a snippet from
[web.dev](https://web.dev/learn/css/grid/#the-minmax()-function) that explains
what `minmax(0, 1fr)` is really doing.

> To force a track to take an equal share of the space in the grid container minus
gaps use minmax. Replace 1fr as a track size with minmax(0, 1fr). This makes the
minimum size of the track 0 and not the min-content size. Grid will then take
all of the available size in the container, deduct the size needed for any gaps,
and share the rest out according to your fr units.

---

# Learn More

- [Reconsider the meaning of 1fr](https://github.com/w3c/csswg-drafts/issues/1777)
- [A Deep Dive Into CSS Grid minmax()](https://ishadeed.com/article/css-grid-minmax/)
- [Full-Bleed Layout Using CSS Grid](https://www.joshwcomeau.com/css/full-bleed/)
- [Preventing overflow when using CSS Grid](https://css-tricks.com/preventing-a-grid-blowout/)
- [Position sticky with CSS Grid](https://ishadeed.com/article/position-sticky-css-grid/)