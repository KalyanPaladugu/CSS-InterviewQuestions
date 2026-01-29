
+ What is CSS?
    - CSS is used to style HTML elements. It controls layout, colors, fonts, spacing, and responsiveness
    ```
    <p class="text">Hello CSS</p>
    ```
    we can write style for above html element by class "text" 
    ```
    .text {
    color: blue;
    font-size: 18px;
    }
    ```

+ Types of CSS
    - CSS can be applied in three ways depending on scope and maintainability
```
<!-- Inline -->
<p style="color:red;">Inline</p>

<!-- Internal -->
<style>
  p { color: green; }
</style>

<!-- External -->
<link rel="stylesheet" href="style.css">
```
+ CSS Box Model
    - Defines how element size is calculated: content + padding + border + margin
```
.box {
  width: 200px;
  padding: 20px;
  border: 5px solid black;
  margin: 10px;
}

```
+ Class vs ID
    - Class is reusable; ID is unique and has higher specificity

```
HTML:
<div class="box"></div>
<div id="main"></div>
CSS:
.box { background: lightblue; }
#main { background: orange; }
```
+ Pseudo-class vs Pseudo-element
    - Pseudo-classes style states; pseudo-elements style parts

```
Pseudo-class	Meaning
:hover	        Mouse over
:active	        While clicking
:focus	        Element focused
:focus-visible	Focus via keyboard
:focus-within	Child element focused

Position Pseudo classes:

li:first-child { color: red; }
li:last-child { color: blue; }
li:nth-child(2) { color: green; }

| Pseudo-class         |
| -------------------- |
| `:first-child`       |
| `:last-child`        |
| `:only-child`        |
| `:nth-child(n)`      |
| `:nth-last-child(n)` |

button:hover {
  background: green;
}

```
- Pseudo-elements style parts of elements

```
| Pseudo-element   |
| ---------------- |
| `::first-letter` |
| `::first-line`   |

h1::before {
  content: "🔥 ";
}

h1::after {
  content: " 🔥";
}

p::selection {
  background: yellow;
}
```

+ display:none vs visibility:hidden
    - One removes the element completely; the other only hides it

    ```
    .hidden1 { display: none; }
    .hidden2 { visibility: hidden; }

    ```
+ CSS Specificity
    - Determines which rule wins when multiple rules apply

```
Specificity Order (High → Low)
Rank	Selector Type	Example
1️⃣	!important ⚠️	color: red !important;
2️⃣	Inline styles	<p style="color:red">
3️⃣	ID selector	#header
4️⃣	Class / Attribute / Pseudo-class	.box, [type="text"], :hover
5️⃣	Element / Pseudo-element	div, p, ::before
6️⃣	Universal	*

```

+ Z-index
    - Controls stacking order (who is on top)
    - Works only on positioned elements
    ```
    position: relative | absolute | fixed | sticky;
    ```

    ```
    <div class="box red"></div>
    <div class="box blue"></div>

    .box {
    width: 100px;
    height: 100px;
    position: absolute;
    }

    .red {
    background: red;
    z-index: 1;
    }

    .blue {
    background: blue;
    left: 40px;
    top: 40px;
    z-index: 2;
    }

    ```
    - Blue appear on top
    - z-index Does NOT Work Without Position

+ CSS Positions
    - The position property controls how an element is placed in the page and what it’s positioned relative to
    - position: static (Default)
    ```
        .box {
        position: static;
        }
    ```
    - Default for all elements
    🔹 Follows normal document flow
    🔹 top, left, right, bottom, z-index ❌ don’t work

    - position: relative
         - Moves relative to its original position
        🔹 Space is still reserved
        🔹 Used as a reference for absolute children
    ```
    .box {
        position: relative;
        top: 20px;
        left: 10px;
    }
    ```
    - position: absolute
    ```
    <div class="parent">
        <div class="child"></div>
    </div>
    .parent {
    position: relative;
    }

    .child {
    position: absolute;
    top: 0;
    right: 0;
    }
    ```
    🔹 Positioned relative to nearest positioned ancestor
    🔹 Removed from normal flow
    🔹 If no parent is positioned → relative to <html>
  
  - position: fixed
  ```
  .navbar {
  position: fixed;
  top: 0;
   }
  ```
  🔹 Positioned relative to viewport
  🔹 Stays fixed on scroll
  🔹 Removed from document flow
  - position: sticky (Hybrid ⭐)

  ```
    .header {
    position: sticky;
    top: 0;
    }
 
  ```
  🔹 Acts like relative initially
  🔹 Becomes fixed when scrolling
  🔹 Needs a scrollable parent
  🔹 Requires top, left, etc.

+ Flexbox
  - One-dimensional layout system for alignment.
```
.container {
  display: flex;
  justify-content: center;
  align-items: center;
}
```

+ Flexbox vs Grid

Explanation:
- Flexbox = 1D layout, Grid = 2D layout.

```
.flex { display: flex; gap: 10px; }

.grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
}
```
+ nth-child vs nth-of-type

Explanation:
+ One counts all nodes; the other counts element type.

```
li:nth-child(2) { color: red; }
p:nth-of-type(2) { color: blue; }
```

+ Media Queries

Explanation:
- Apply styles based on device size.

```
@media (max-width: 768px) {
  body {
    background: lightgray;
  }
}
```
+ CSS Optimization

Explanation:
- Avoid deep selectors.

```
/* Bad */
.container div ul li span {}

/* Good */
.list-item {}
```


