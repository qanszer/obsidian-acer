
2025-10-21  13:29

Tags: [[Odin]] [[JavaScript]] [[Coding]]

---

**General rule for clean code:**

"one line --- one action"


For string to number conversion:

```js
Number()
```


For rounding off:

```js
.toFixed(2);
```


For comparison:

```js
===  // is equal to (including datatype)
!==  // is not equal to (including datatype)
```


To recognize inline ' or " inside a string, use backslash \

```js
const bigmouth = 'I\'ve got no right to take my place...'; console.log(bigmouth);
```


Passing an empty input to a prompt returns an empty string `''`:
Pressing ESC during a prompt returns `null`:

```js
else if (visitor == "" || visitor == null) {
	alert("Canceled");
}
```






---
# References


### Main Reference - TheOdinProject
https://www.theodinproject.com/lessons/foundations-variables-and-operators

### Variables
https://javascript.info/variables#variable-naming
https://javascript.info/types
### Numbers
https://www.w3schools.com/js/js_arithmetic.asp
https://www.w3schools.com/js/js_numbers.asp
https://developer.mozilla.org/en-US/docs/Learn_web_development/Core/Scripting/Math
https://javascript.info/operators

### Strings
https://developer.mozilla.org/en-US/docs/Learn_web_development/Core/Scripting/Strings
https://www.w3schools.com/js/js_string_methods.asp
https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String