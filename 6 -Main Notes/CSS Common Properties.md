
2025-09-14  18:15

Tags:  [[Coding]] [[CSS]] 

# CSS Cheat Sheet

[https://htmlcheatsheet.com/css/](https://htmlcheatsheet.com/css/)

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

#### Alignment

![[Pasted image 20250929184104.png]]

justify-content: primary axis
align-items: cross axis

- `justify` — to position something along the _primary axis_.
    
- `align` — to position something along the _cross axis_.
    
- `content` — a group of “stuff” that can be distributed.
    
- `items` — single items that can be positioned individually.

For space between flex items:
gap







# References
https://www.theodinproject.com/lessons/foundations-intro-to-css
