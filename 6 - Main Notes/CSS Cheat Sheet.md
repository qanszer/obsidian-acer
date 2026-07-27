
2025-09-14  18:15

Tags:  [[Coding]], [[CSS]], [[The Odin Project]]

# CSS Cheat Sheet

[https://htmlcheatsheet.com/css/](https://htmlcheatsheet.com/css/)


### Overview Guide

```CSS
color
background-color
font-family
font-size
font-weight (boldness)
text-align (horizontal)
```

```CSS
class="placeholder"
.placeholder
  
id="placeholder"
#placeholder 
/* avoid using id too much */
  
chain selectors
.first-class.second-class
.first-class#1st-id
  
descendant combinator
.parent-class .child-class
```

```CSS

#p1 {background-color: #ff0000;}   /* red hex */
#p1a {background-color: #ff000080;}   /* red transparency */

#p1 {background-color: rgb(255, 0, 0);}   /* red rgb */
#p1 {background-color: rgba(255, 0, 0, 0.3);}   /* red with opacity rgba */

#p1 {background-color: hsl(120, 100%, 50%);}   /* green hsl */
#p1 {background-color: hsla(120, 100%, 50%, 0.3);}   /* green with opacity */

#p1 {background-color: blue;}

The **currentcolor** keyword refers to the value of the color property of an element:
#myDIV {
  color: blue; /* Blue text color */
  border: 10px solid currentcolor; /* Blue border color */
}

```

**display: inline-block** = width, height, and padding are respected

![[Pasted image 20250918000330.png]]

![[Pasted image 20250929160323.png]]

### Alignment

![[Pasted image 20250929184104.png]]

justify-content: primary axis
align-items: cross axis

- `justify` — to position something along the _primary axis_.
    
- `align` — to position something along the _cross axis_.
    
- `content` — a group of “stuff” that can be distributed.
    
- `items` — single items that can be positioned individually.


For space between flex items:
gap

Opacity
- value is between 0 to 1
- example: 0.5
- When you use `opacity` you make the element and everything inside it transparent, whereas using RGB or hex with an alpha parameter only makes the color you are specifying transparent.


### Add font:

```css
<link rel="stylesheet" href="https://fonts.googleapis.com/css?family=Geist">
```


### Vertically center an element on the left:

```css
.toolbar {
	position: fixed;
	left: 0;
	top: 50%;
	transform: translateY(-50%);
}
```


### Keep aspect ratio

```css
/* full-width * aspect-ratio */
.full-width {
  width: 100vw;
  height: calc(100vw * (9/16));
}
```


### Text Styles

```css
font-style: italic;
letter-spacing: 0.5rem;
line-height: 1.5;
text-transform: uppercase;
text-shadow: ;

/* ellipsis (...) for overflowing text */
.overflowing {
  white-space: nowrap;
  overflow: hidden;
  text-overflow: ellipsis;
}
```



---

# CSS Good Practices


## General Good Practices


**System Font Stack:**

```css
html {
  font-family: system-ui, "Segoe UI", Roboto, Helvetica, Arial, sans-serif, "Apple Color Emoji", "Segoe UI Emoji", "Segoe UI Symbol";
}
```


Avoid using id too much


Combine selectors of common properties:
```css
.class1, class.2 {
	color: white;
	text-align: center:
}
```

If you wanted to adjust the size of the image without causing it to lose its proportions, you would use a value of “auto” for the height property and adjust the width value:
```css
img {
  height: auto;
  width: 500px;
}
```

Order of values:
padding: (top/bottom)px (left/right)px (bottom)px (right)px;

Remove link underline:
```css
text-decoration: none;
```

Ensures container takes full viewport height:
```css
min-height: 100vh; 
```

For max size:
```css
width: 100vw;
height: 100vh;
```

Vertically center inline texts like header links:
do 
```css
align-items: center; 
```
on the main navbar container


For unordered lists (ul) :
```css
ul {
	list-style-type: none;
	padding: 0;
	margin: 0;
	gap: 20px;
}
```

To avoid a container shrinking by itself:
```css
flex-shrink: 0;
```

Take up whole space:
```css
width: 100%;
```


For non-moving background:
```css
background: url() no-repeat center center fixed;
background-size: cover;
```


Center horizontally:
```css
.container {
	width: 980px; margin: 0 auto;
}
```

In this example, two things are done to center this element horizontally within the available space:

- The element is given a specified width
- The left and right margins are set to `auto`


---

## CSS Resets

The purpose of CSS Resets is to match the styling for all browsers, while at the same time improve the defaults of the styling.

#### 1 - Personal

```css
html {
	box-sizing: border-box;
	scroll-behavior: smooth;
}

*, *::before, *::after {
	box-sizing: inherit;
}

* {
	margin: 0px;
	padding: 0px;
}

a {
	text-decoration: none;
	cursor: pointer;
	user-select: none;
}

ul {
	list-style-type: none;
	padding: 0;
	margin: 0;
}

body {
	display: flex;
	flex-direction: column;
	height: 100vh;
}

[id] { 
	scroll-margin-top: 150px; 
}

::selection {
	background-color: ;
	color: ;
}
```

#### 2 - Matt Brictson

```css
/*! modern-normalize v3.0.1 | MIT License | https://github.com/sindresorhus/modern-normalize */

*,
::before,
::after {
    box-sizing: border-box;
}

html {
    font-family:
        system-ui,
        'Segoe UI',
        Roboto,
        Helvetica,
        Arial,
        sans-serif,
        'Apple Color Emoji',
        'Segoe UI Emoji'; /* 1 */
    line-height: 1.15; /* 2 */
    -webkit-text-size-adjust: 100%; /* 3 */
    tab-size: 4; /* 4 */
}

body {
    margin: 0;
}

b,
strong {
    font-weight: bolder;
}

code,
kbd,
samp,
pre {
    font-family:
        ui-monospace,
        SFMono-Regular,
        Consolas,
        'Liberation Mono',
        Menlo,
        monospace; /* 1 */
    font-size: 1em; /* 2 */
}

small {
    font-size: 80%;
}

sub,
sup {
    font-size: 75%;
    line-height: 0;
    position: relative;
    vertical-align: baseline;
}

sub {
    bottom: -0.25em;
}

sup {
    top: -0.5em;
}

table {
    border-color: currentcolor;
}

button,
input,
optgroup,
select,
textarea {
    font-family: inherit; /* 1 */
    font-size: 100%; /* 1 */
    line-height: 1.15; /* 1 */
    margin: 0; /* 2 */
}

button,
[type='button'],
[type='reset'],
[type='submit'] {
    -webkit-appearance: button;
}

legend {
    padding: 0;
}

progress {
    vertical-align: baseline;
}

::-webkit-inner-spin-button,
::-webkit-outer-spin-button {
    height: auto;
}

[type='search'] {
    -webkit-appearance: textfield; /* 1 */
    outline-offset: -2px; /* 2 */
}

::-webkit-search-decoration {
    -webkit-appearance: none;
}

::-webkit-file-upload-button {
    -webkit-appearance: button; /* 1 */
    font: inherit; /* 2 */
}

summary {
    display: list-item;
}

/* Matt Brictson */

:root {
  line-height: 1.5;
}

h1, h2, h3, h4, h5, figure, p, ol, ul {
  margin: 0;
}

ol[role="list"], ul[role="list"] {
  list-style: none;
  padding-inline: 0;
}

h1, h2, h3, h4, h5 {
  font-size: inherit;
  font-weight: inherit;
}

img {
  display: block;
  max-inline-size: 100%;
}
```

#### 3 - Josh Comeau

```js
/*
  Josh's Custom CSS Reset
  https://www.joshwcomeau.com/css/custom-css-reset/
*/

*, *::before, *::after {
  box-sizing: border-box;
}

*:not(dialog) {
  margin: 0;
}

@media (prefers-reduced-motion: no-preference) {
  html {
    interpolate-size: allow-keywords;
  }
}

body {
  line-height: 1.5;
  -webkit-font-smoothing: antialiased;
}

img, picture, video, canvas, svg {
  display: block;
  max-width: 100%;
}

input, button, textarea, select {
  font: inherit;
}

p, h1, h2, h3, h4, h5, h6 {
  overflow-wrap: break-word;
}

p {
  text-wrap: pretty;
}
h1, h2, h3, h4, h5, h6 {
  text-wrap: balance;
}

#root, #__next {
  isolation: isolate;
}
```


---

## Web Fonts

### Nuance

Manual method (self-hosting) is only faster if your site uses a Content Delivery Network (CDN) and HTTP/2. Otherwise the automatic method beats self-hosting.
[More info](https://web.dev/articles/font-best-practices#use_self-hosted_fonts)

*Checking via Command Line (cURL):*
- Open your terminal or command prompt.
- Run the command: `curl -I --http2 https://<your-github-username>.github.io/<repo-name>/`
- If it says `HTTP/2 200`, your site is successfully running HTTP/2.
- If it says `via: 1.1 varnish`, your site is successfully running CDN.

### 1 - Manual Method
For production sites where every millisecond matters
[More info](https://developer.mozilla.org/en-US/docs/Learn_web_development/Core/Text_styling/Web_fonts#generating_the_required_code)

- Find a free font distributor and download there: This is a site that makes free fonts available for download (there may still be some license conditions, such as crediting the font creator). Examples include [Font Squirrel](https://www.fontsquirrel.com/ "External link (opens in new tab)"), [DaFont](https://www.dafont.com/ "External link (opens in new tab)"), and [Everything Fonts](https://everythingfonts.com/ "External link (opens in new tab)").
- Unzip them and choose 1 file from each font's directory to convert on [Transfonter Webfont Generator](https://transfonter.org/ "External link (opens in new tab)"). Click *Add fonts* button and choose each selected font file. Click *Convert* and then *Download*.
- Unzip the downloaded file on the repo directory (with the html and css). Rename the unzipped file to `fonts`.
- Copy the css files inside the `fonts` directory to your main css file and adjust the url with `fonts/`:
```css
/* only use woff2 */
@font-face {
	font-family: 'Vogue';
	src: url('fonts/Vogue-Regular.woff2') format('woff2'),
	font-weight: normal;
	font-style: normal;
	font-display: swap;
}
```
- Add this to html inside `<head` and before your main css `<link>` element (adjust href as needed):
```html
<link rel="preload" href="fonts/Vogue-Regular.woff2" as="font" type="font/woff2" crossorigin>
<link rel="preload" href="fonts/AltoneTrial-Regular.woff2" as="font" type="font/woff2" crossorigin>
```
- Use it normally on your font stacks
```css
html {
	font-family: "Vogue", system-ui, "Segoe UI", Roboto, Helvetica, Arial, sans-serif, "Apple Color Emoji", "Segoe UI Emoji", "Segoe UI Symbol";
}
```

### 2 - Automatic Method
For small projects where convenience matters
[More info](https://developer.mozilla.org/en-US/docs/Learn_web_development/Core/Text_styling/Web_fonts#using_an_online_font_service)

- Go to [Google Fonts](https://fonts.google.com/). Find your selected font and click *Get font*. Click *Get embed code*.
- Copy the `<link>` elements before your main css `<link>` element
- Use it normally on your font stacks
```css
html {
	font-family: "Google Sans", system-ui, "Segoe UI", Roboto, Helvetica, Arial, sans-serif, "Apple Color Emoji", "Segoe UI Emoji", "Segoe UI Symbol";
}
```


### Font Best Practices
https://web.dev/articles/font-best-practices

- Two approaches can be combined: for example, use `font-display: swap` for branding and other visually distinctive page elements. Use `font-display: optional` for fonts used in body text.
```css
html {
	font-family: "Google Sans", system-ui, "Segoe UI", Roboto, Helvetica, Arial, sans-serif, "Apple Color Emoji", "Segoe UI Emoji", "Segoe UI Symbol";
	font-display: optional;
}

h1, h2, h3 {
	font-family: "Vogue", system-ui, "Segoe UI", Roboto, Helvetica, Arial, sans-serif, "Apple Color Emoji", "Segoe UI Emoji", "Segoe UI Symbol";
	font-display: swap;
}
```

- When possible, replace icon fonts with SVGs, which is also better for accessibility. Newer versions of popular icon fonts typically support SVG. For more information on switching to SVGs, see [Font Awesome](https://fontawesome.com/v5.15/how-to-use/on-the-web/advanced/svg-sprites) and [Material Icons](https://google.github.io/material-design-icons/#svg).


---

## Typography

### Scaling and Clamping Text

Ideal way to scale text based on viewer width:
```css
html {
  font-size: clamp(1rem, 0.75rem + 1.5vw, 2rem);
}
```
- 1st value is min size
- 2nd value is same as `calc()`
- 3rd value is max size

### Line Length

In his classic book [_The Elements of Typographic Style_](http://webtypography.net/2.1.2), Robert Bringhurst had this to say on line length (or measure):

> Anything from 45 to 75 characters is widely regarded as a satisfactory line length for a single-column page set in a serifed text face in a text size. The 66-character line (counting both letters and spaces) is widely regarded as ideal. For multiple column work, a better average is 40 to 50 characters.

```css
article {
  max-inline-size: 66ch;
}
```
- Using `ch` units for width will cause new lines to wrap at the 66th character at that font size.

### Line Height

Use unitless values for your `line-height` declarations. This ensures that the line height is relative to the `font-size`.
```css
line-height: 24px; /*  wrong  */
line-height: 1.5;  /* correct */
```

Shorter lines of text can have larger `line-height` values. But if you use large `line-height` values for long lines of text, it's hard for the reader's eye to move from the end of one line to the start of the next line.
```css
article {
  max-inline-size: 66ch;
  line-height: 1.65;
}
blockquote {
  max-inline-size: 45ch;
  line-height: 2;
}
```

### Hierarchy

Remember to prioritize hierarchy as you build your user interfaces for better clarity and page flow. A great way to do this is with [a typography scale built into your design system](https://material.io/design/typography/the-type-system.html#type-scale).

### Variable Fonts

If you are using lots of different weights or styles of the same typeface, you may end up using lots of separate font files—a separate font file for each weight or style.

[Variable fonts](https://web.dev/articles/variable-fonts) solve this problem by using one file. Instead of having separate files for regular, bold, extra bold, and other variants, a variable font file is responsive. It contains all the information it needs to be displayed across a spectrum of weights or styles.

If you're styling elements using the `system-ui` value for `font-face` property, you might get all the benefits of variable fonts without downloading any font files. [More and more system fonts are now variable fonts](https://web.dev/blog/more-variable-font-options-in-chromium-83).


---

## Responsiveness

#### Fonts:

Use `rem` or `em` (most responsive)

```css
/* ✓ Best - scales with user preferences */
body { font-size: 16px; }  /* Base size */
h1 { font-size: 2.5rem; }   /* 40px */
h2 { font-size: 2rem; }     /* 32px */
p { font-size: 1rem; }      /* 16px */

/* Good alternative */
h1 { font-size: clamp(1.5rem, 5vw, 3rem); }  /* Fluid sizing */
```

**Why `rem`?**

- Scales with root font size
- Respects user's browser settings
- Easy to adjust everything at once


#### **Containers/Widths:**

Use `%`, `max-width`, or `vw`

```css
/* ✓ Best for containers */
.container {
    width: 90%;           /* Responsive to parent */
    max-width: 1200px;    /* Don't get too wide */
    margin: 0 auto;       /* Center it */
}

/* Full width sections */
.hero {
    width: 100%;
    max-width: 100vw;
}
```


#### **Heights:**

Use `vh` for full-screen, `auto` for content-based

```css
/* ✓ Full viewport height */
.hero {
    min-height: 100vh;  /* At least full screen */
}

/* ✓ Let content determine height */
.card {
    height: auto;
}

/* ❌ Avoid fixed pixel heights */
.section {
    height: 500px;  /* Won't adapt well */
}
```


### **Spacing (padding/margin):**

Use `rem` or `%`

```css
/* ✓ Best - scales with font size */
.card {
    padding: 2rem;      /* 32px if base is 16px */
    margin: 1.5rem 0;
}

/* Good for responsive spacing */
.section {
    padding: 5% 10%;    /* Relative to container */
}

/* ❌ Avoid fixed pixels for large spacing */
.hero {
    padding: 100px;  /* Too rigid */
}
```


### **Media queries:**

Use `em` for breakpoints

```css
/* ✓ Use em for media queries (more reliable) */
@media (max-width: 48em) {  /* 768px */
    .navbar {
        flex-direction: column;
    }
}

@media (max-width: 64em) {  /* 1024px */
    .container {
        width: 95%;
    }
}
```


### Unexpected shrink problem

If one div child shrinked because of `align-items: center`, add `width: 100%` to the child



---

# References

https://www.theodinproject.com/lessons/foundations-intro-to-css