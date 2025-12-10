
2025-09-14  18:20

Tags:  [[CSS]] [[Coding]]

---

# CSS Good Practices


## Personal CSS Template:

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
}

[id] { 
	scroll-margin-top: 150px; 
}

::selection {

background-color: ;

color: ;

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

Use `rem`, `em`, or `%`

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