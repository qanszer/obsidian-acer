
2025-09-14  18:20

Tags:  [[CSS]] [[Coding]]

# CSS Good Practices

Personal CSS Template:

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


# References

https://www.theodinproject.com/lessons/foundations-intro-to-css