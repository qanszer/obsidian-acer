
2025-09-14  18:38

Tags: [[HTML]] [[Coding]]

# HTML Cheat Sheet

https://htmlcheatsheet.com/

Standard template:
Type "!"
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








---

# References

https://www.theodinproject.com/lessons/foundations-html-boilerplate
https://www.theodinproject.com/lessons/foundations-working-with-text
https://www.theodinproject.com/lessons/foundations-links-and-images
