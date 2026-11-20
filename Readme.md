
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
###### Two types of Box Sizing

1. content-box (Default)

```.box {
  width: 200px;
  padding: 20px;
  border: 5px solid black;
  box-sizing: content-box;
}
```
- Total width = 200 + 40 + 10 = 250px (excluding margin).
2. border-box

```.box {
  width: 200px;
  padding: 20px;
  border: 5px solid black;
  box-sizing: border-box;
}
```
- Total width = 200px (excluding margin).

- Why do we use box-sizing: border-box?

Answer:
- We use box-sizing: border-box to include padding and border within the specified width and height.

- It makes layouts easier to manage and prevents unexpected element size increases.

+ Class vs ID
    - Class is reusable; ID is unique and has higher specificity
- HTML:
```
<div class="box"></div>
<div id="main"></div>
CSS:
.box { background: lightblue; }
#main { background: orange; }
```
##### CSS Specificity
- CSS Specificity is a set of rules used by the browser to decide which CSS style should be applied when multiple CSS selectors target the same HTML element.

| Selector type | Specificity |
| :--- | :--- |
| Inline styles | 1000 |
| ID selector (`#id`) | 100 |
| Class, attribute, pseudo-class | 10 |
| Element, pseudo-element | 1 |
| Universal selector (`*`) | 0 |

- `!important` overrides normal declarations in the cascade, regardless of ordinary selector specificity.
```
<head>
<style type="text/css" media="all">
  p {
    color: red !important;
  }

  #heading {
    color: blue;
  }
    </style>
  </head>
  <body>
      <p id="heading" class="text">Hello World</p>
  </body>
```


+ Pseudo-class vs Pseudo-element
  - Pseudo-class: Selects an element based on its state or position.
  - Pseudo-element: Styles a specific part of an element or inserts generated content.

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
    - There are 5 main types of CSS positioning:
        1. static
        2. relative
        3. absolute
        4. fixed
        5. sticky
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
- :nth-child() selects an element based on its position among all sibling elements.
- :nth-of-type() selects an element based on its position among siblings of the same HTML element

- :nth-child()
- It selects an element based on its position among all sibling elements.

HTML:
```<div>
  <p>Paragraph 1</p>
  <h2>Heading</h2>
  <p>Paragraph 2</p>
  <p>Paragraph 3</p>
</div>
```


CSS:
```
p:nth-child(2) {
  color: red;
}
```
- Output: No paragraph will become red.
  - Because the second child is an h2, not a p.

- :nth-of-type()
- It selects an element based on its position among siblings of the same HTML element type.

```
p:nth-of-type(2) {
  color: red;
}
```
- Paragraph 2 becomes red.
- Why?
- Because nth-of-type(2) counts only the <p> elements.

+ Media Queries

Explanation:
- Apply styles based on device size.
- Examples of Media Queries

1: Mobile devices

```
/* Mobile */
@media (max-width: 480px) {
  .container {
    width: 100%;
    background-color: lightblue;
  }
}
```

Example 2: Tablets
```
/* Tablet */
@media (min-width: 481px) and (max-width: 768px) {
  .container {
    width: 90%;
    background-color: lightgreen;
  }
}
```

Example 3: Desktop
```
/* Desktop */
@media (min-width: 769px) {
  .container {
    width: 80%;
    background-color: lightcoral;
  }
}
```

######  CSS Optimization
- CSS optimization helps improve rendering performance, maintainability, and user experience.

1. Avoid unnecessary CSS selectors
- Avoid writing deeply nested selectors because they make CSS harder to maintain and can increase selector matching complexity.

- Avoid deep selectors.

```
/* Bad */
.container div ul li span {}

/* Good */
.list-item {}
```

2. Remove duplicate CSS
- Avoid repeating the same styles in multiple places.
```
Avoid
.button1 {
  background: blue;
  padding: 10px;
}

.button2 {
  background: blue;
  padding: 10px;
}
```

- Prefer
```
.button {
  background: blue;
  padding: 10px;
}

.button1 {
  /* Additional styles */
}

.button2 {
  /* Additional styles */
}
```

3. Use CSS shorthand properties
- Instead of writing multiple properties separately, use shorthand wherever appropriate.

- Avoid
```
.box {
  margin-top: 10px;
  margin-right: 20px;
  margin-bottom: 10px;
  margin-left: 20px;
}
```
- Prefer
```
.box {
  margin: 10px 20px;
}
```

4. Use Flexbox and Grid instead of unnecessary positioning

- Avoid using position: absolute for every layout requirement.
- Avoid

```.container {
  position: relative;
}

.box1 {
  position: absolute;
  left: 20px;
}

.box2 {
  position: absolute;
  left: 150px;
}
```


- Prefer
```
.container {
  display: flex;
  gap: 20px;
  align-items: center;
}
```
5. Optimize images and fonts

Some best practices:
- Use WebP or AVIF image formats where suitable.
- Compress images without losing unnecessary quality.
- Use lazy loading for below-the-fold images.
- Use appropriate image dimensions.
- Avoid loading unnecessary font weights.
- Use modern font formats such as WOFF2.

```<img
  src="employee.webp"
  alt="Employee"
  loading="lazy"
  width="300"
  height="200"
/>
```
6. Use CSS animations efficiently
- For smoother animations, prefer transform and opacity where possible.
- Less ideal
```
.box:hover {
  left: 20px;
  width: 200px;
}
```
- Prefer
```
.box {
  transition: transform 0.3s ease;
}

.box:hover {
  transform: translateX(20px);
}
```

Why?

- transform and opacity can often be handled efficiently by the browser's compositing process, whereas properties such as width, height, and positional layout properties can trigger layout or painting work.

7. Use CSS media queries for responsive design
8. Remove unused CSS
9. Minify CSS
- Minification removes unnecessary whitespace and comments from CSS files.
10. Use CSS variables
- CSS variables help maintain consistent styles and reduce repeated values.
```
:root {
  --primary-color: blue;
  --spacing: 16px;
}

.button {
  background: var(--primary-color);
  padding: var(--spacing);
}

.card {
  border-color: var(--primary-color);
  padding: var(--spacing);
}
```
- This improves maintainability, especially in large React applications.
