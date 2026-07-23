
2025-09-14  18:38

Tags: [[HTML]] [[Coding]] [[The Odin Project]]

---

# HTML Cheat Sheet

https://htmlcheatsheet.com/
https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements

Standard template:
Type "!"

**Custom boilerplate:**
Type "5html"

```html
<link rel="stylesheet" href="style.css">
```

Make comment:
Press ctrl + /

Open other page on same website:
Type "./directory/file.html"

Open anchor link in new tab with security:
Add
```html
href="link" target="_blank" rel="noopener noreferrer" 
```
 to anchor element


Scroll to page section:
-  add an ID to an element
-  make an anchor link with its link to the id
```css
link="main"
```



***Useful HTML Abbreviations
```html
nav>ul>li

li*5

a{link text here}

div.first.second

div#id
```


Shortcut for relative file path:
ctrl + shift + h


All block-level elements in HTML:
![[Pasted image 20250917235607.png]]

All inline-level elements in HTML:
![[Pasted image 20250917235731.png]]

Note: an inline element cannot contain a block-level element!



## Live Server on Mobile

1. Find the ipv4 addresss of the current wifi of laptop (192.168.1.1)
2. Look at the port of the live server in laptop (:5500)
3. Type this in a browser on mobile:
		`http://ipv4address:5500/index.html`


## DOM (Document Object Model)

It is the browser's blueprint or object model of your web page. It is what Javascript uses to find, alter, or add elements to build interactive websites.

The DOM is **not** the original HTML source code; it's the browser's in-memory object representation of that code, reflecting the page's current state, including all modifications.


## Add Icon on Tabs Section

https://favicon.io/favicon-converter/


---

## SVG
[More info](https://www.theodinproject.com/lessons/node-path-intermediate-html-and-css-svg)

SVGs are often used for:
1. Icons
2. Graphs/Charts
3. Large, simple images
4. Patterned backgrounds
5. Applying effects to other elements via SVG filters

Not used for:
- If your image is supposed to be photo-realistic, or it has fine detail or texture (“[grunge textures](https://unsplash.com/s/photos/grunge-texture)” are a great example), then SVGs are the wrong tool for the job.

**Anatomy of SVG**
https://www.theodinproject.com/lessons/node-path-intermediate-html-and-css-svg#anatomy-of-an-svg

### **Complete List of SVG Elements**
https://developer.mozilla.org/en-US/docs/Web/SVG/Element

Many SVG attributes, such as `fill` and `stroke`, can be changed in your CSS. Learn more in this [article on SVG properties and CSS](https://css-tricks.com/svg-properties-and-css/).


### **2 Methods of Using SVGs**

Linking SVGs works basically the same way as linking any other image. You can use an HTML image element such as `<img>`, or link it in your CSS using `background-image: url(./my-image.svg)`. They will still scale properly, but the contents of the SVG will not be accessible from the webpage.

The alternative is to inline your SVGs by pasting their contents directly into your webpage’s code, rather than linking to it as an image. It will still render correctly, but the SVG’s properties will be visible to your code, which will allow you to alter the image dynamically via CSS or JavaScript.

Inlining SVGs allows you to unlock their full potential, but it also comes with some serious drawbacks: it makes your code harder to read, makes your page less cacheable, and if it’s a large SVG it might delay the rest of your HTML from loading.

Some of the drawbacks of inlining SVG code can be avoided once you’ve learned a front-end JavaScript library like React, or a build-tool like webpack.

**Linking is generally cleaner and simpler, so prefer that unless you need to tweak the SVG code alongside your HTML.**


### Guide to Tweaking SVGs
[More info](https://www.joshwcomeau.com/svg/friendly-introduction-to-svg/#hello-svg-1)

### Create Regular Polygons
[More info](https://www.joshwcomeau.com/svg/friendly-introduction-to-svg/#hello-svg-1:~:text=To%20create%20regular%20polygons)

### Proper SVG Formatting

```html
// proper
<polygon
  points="
    60,100
    100,180
    140,140
    180,180
    220,100
  "
/>
```

```html
// improper
<polygon points="60 100 100 180 140 140 180 180 220 100" />
```


### Scalable Handmade SVGs
[More info](https://www.joshwcomeau.com/svg/friendly-introduction-to-svg/#hello-svg-1:~:text=The%20viewBox%20attribute)


---

## Tables

#### Example of a proper HTML table:

```html
<table>
    <caption>My Concerts 🎸</caption>
    <thead>
        <tr>
            <th scope="col">Artist</th>
            <th scope="col">Location</th>
            <th scope="col">Cost</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>Blur</td>
            <td>Exeter</td>
            <td>£50</td>
        </tr>
        <tr>
            <td>Billie Eilish</td>
            <td>London</td>
            <td>£90</td>
        </tr>
        <tr>
            <td>The Weeknd</td>
            <td>Glasgow</td>
            <td>£110</td>
        </tr>
        <tr>
            <td>Adele</td>
            <td>Bristol</td>
            <td>£65</td>
        </tr>
    </tbody>
    <tfoot>
        <tr>
            <td colspan="2">Sum</td>
            <td>£315</td>
        </tr>
    </tfoot>
</table>
```

```css
html, body {
    margin: 0;
    padding: 25px;
    font-family: Verdana, Geneva, Tahoma, sans-serif;
}

body {
    font-size: 20px;
}

caption {
    margin-bottom: 14px;
    font-size: 30px;
}

th {
    background-color: #374d7c;
    color: #fff;
}

table {
    border-radius: 5px;
    margin: 0 auto;
}

td {
    background-color: #fdf289;
}

td, th {
    padding: 10px 20px;
}

tfoot td {
    background-color: #46edc8;
    text-align: center;
}
```


#### Example with `colgroup` and `col`:

```html
<table>
  <caption>School language timetable</caption>
  <colgroup>
    <col span="2" />
    <col class="column-background" />
    <col class="column-fixed-width" />
    <col class="column-background" />
    <col class="column-background-border" />
    <col span="2" class="column-fixed-width" />
  </colgroup>
  <tr>
    <td>&nbsp;</td>
    <th>Mon</th>
    <th>Tues</th>
    <th>Wed</th>
    <th>Thurs</th>
    <th>Fri</th>
    <th>Sat</th>
    <th>Sun</th>
  </tr>
  <tr>
    <th>1st period</th>
    <td>English</td>
    <td>&nbsp;</td>
    <td>&nbsp;</td>
    <td>German</td>
    <td>Dutch</td>
    <td>&nbsp;</td>
    <td>&nbsp;</td>
  </tr>
  <tr>
    <th>2nd period</th>
    <td>English</td>
    <td>English</td>
    <td>&nbsp;</td>
    <td>German</td>
    <td>Dutch</td>
    <td>&nbsp;</td>
    <td>&nbsp;</td>
  </tr>
  <tr>
    <th>3rd period</th>
    <td>&nbsp;</td>
    <td>German</td>
    <td>&nbsp;</td>
    <td>German</td>
    <td>Dutch</td>
    <td>&nbsp;</td>
    <td>&nbsp;</td>
  </tr>
  <tr>
    <th>4th period</th>
    <td>&nbsp;</td>
    <td>English</td>
    <td>&nbsp;</td>
    <td>English</td>
    <td>Dutch</td>
    <td>&nbsp;</td>
    <td>&nbsp;</td>
  </tr>
</table>
```

```css
.column-background {
  background-color: #97db9a;
}

.column-fixed-width {
  width: 40px;
}

.column-background-border {
  background-color: #dcc48e;
  border: 4px solid #c1437a;
}
```


#### Example with `colspan`:

```html
<td colspan="number_of_columns">Cell Content</td>
```



---

# References

https://www.theodinproject.com/lessons/foundations-html-boilerplate
https://www.theodinproject.com/lessons/foundations-working-with-text
https://www.theodinproject.com/lessons/foundations-links-and-images
