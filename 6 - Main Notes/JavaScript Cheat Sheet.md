
2025-10-21  13:28

Tags: [[JavaScript]] [[Coding]]

---

# 01 - Numbers


## Arithmetic Operators

[More Info](https://www.w3schools.com/js/js_arithmetic.asp)

The following are all of the operators in Javascript:

| Operator      - | Description                           x |
| --------------- | --------------------------------------- |
| +               | Addition                                |
| -               | Subtraction                             |
| *               | Multiplication                          |
| **              | Exponent                                |
| /               | Division                                |
| %               | Modulo (remainder)                      |
| ++              | Increment                               |
| --              | Decrement                               |


## Number Type

Javascript numbers are always stored as double precision floating point numbers.

Other programming languages have:

1. Whole numbers (integers)
	-  8-bit ---- byte
	- 16-bit --- short
	- 32-bit --- int
	- 64-bit --- long
2. Real numbers (floating point)
	- 32-bit --- float
	- 64-bit --- double (this is always javascript's )

**Javascript numbers are always double** (64-bit floating point).


## Precision

Integers (numbers without a period or exponent notation) are accurate up to 15 digits. 

The maximum number of decimals is 17.

```javascript
let x = 999999999999999;   // x will be 99999 99999 99999 
let y = 9999999999999999;  // y will be 10 00000 00000 00000
```


Floating points (numbers with a period or exponent notation) on the other hand are not always 100% accurate

```js
let x = 0.2 + 0.1;   // output is 0.30000000000000004
```

To solve the problem above, it helps to multiply and divide:

```js
let x = (0.2 * 10 + 0.1 * 10) / 10;   // output is 0.3
```


## Number Problems

Javascript uses the + operator for both addition(numbers) and concatenation(strings). This creates unexpected outcomes for beginners.

```js
x = "10" + "20";       // 1020
x = "10" + 20;         // 1020
x = 10 + "20";         // 1020
```

But **aside from the + operator, all other operators work arithmetically** even when the number is a string.

```js
x = "10" * 20;   // 200
x = "10" / 20;   // 0.5
x = "10" - 20;   // -10
x = "10" ** 20;   // 10000000
```


## Reserved Words

`NaN` is a Javascript reserved word indicating that a number is not a legal number. You can use the global JavaScript function `isNaN()` to find out if a value is a not a number.

`Infinity` (or `-Infinity`) is the value JavaScript will return if you calculate a number outside the largest possible number. Division by 0 (zero) also generates `Infinity`.

Both `Nan` and `Infinity` are considered numbers in Javascript.


## Conversions

[More Info](https://www.w3schools.com/js/js_numbers.asp)

By default, JavaScript displays numbers as base 10 decimals.
But you can use the `toString()` method to output numbers from base 2 to base 36.

```js
let myNumber = 32;  
myNumber.toString(32); // idk
myNumber.toString(16); // hexadecimal
myNumber.toString(12); // idk
myNumber.toString(10); // decimal
myNumber.toString(8);  // octal
myNumber.toString(2);  // binary
```


You can **convert strings into numbers** through `Number()`.

Another method is by using + before the variable/string like:
```js
let apples = "2";
let oranges = "3";

alert (+apples + +oranges);  // 5
alert (Number(apples) + Number(oranges)); // 5
```

the `Number()` function is recommended for clarity.


Other useful math object methods include:

```js
Math.random() * 10;  // random num between 0 and 10
// Generates a random decimal number between 0 (inclusive) and 1 (exclusive). 

Math.floor(4.9)  // 4
// Rounds a number down to the nearest integer

// Random integer from 0 to 9
Math.floor(Math.random() * 10);


Math.ceil(4.9)  // 5
// Rounds a number up to the nearest integer

Math.round(4.9)  // 5
// Rounds a number to the nearest integer
```


For rounding off by your decided number:

```js
.toFixed(2);
```


## Comparison Operators

[More Info](https://javascript.info/comparison)

| Operator   - | Name                                 x |
| ------------ | -------------------------------------- |
| ===          | Strict equality                        |
| !==          | Strict non-equality                    |
| <            | Less than                              |
| >            | Greater than                           |
| <=           | Less than or equal to                  |
| >=           | Greater than or equal to               |

Use `===` and `!==` on Javascript, not the `==` and `!=` because it also tests out whether the datatypes of the values are the same.


## Logical Operators

[More Info](https://javascript.info/logical-operators)

| Operator   - | Name       - | Precedence   - | Description                         x |
| ------------ | ------------ | -------------- | ------------------------------------- |
| \|\|         | OR           | 3rd            | First truth value is returned         |
| &&           | AND          | 2nd            | First false value is returned         |
| !            | NOT          | 1st            | Inverse value is returned             |


**OR Operator When Given Multiple Values:**
https://javascript.info/logical-operators#or-finds-the-first-truthy-value

Practical Usage of OR Operator as a defualt fallback:

```js
function getGreeting(language) {
	const greetings = {
		'en': 'Hello', 
		'es': 'Hola', 
		'fr': 'Bonjour', 
		'de': 'Guten Tag'
	}; return greetings[language] || 'Hello'; // fallback if not found
}
```


**AND Operator When Given Multiple Values:**
https://javascript.info/logical-operators#and-finds-the-first-falsy-value

**NOT Operator**:
https://javascript.info/logical-operators#not


if (!(age >= 14 && age <= 90));

if (age < 14 && age > 90);


## Boolean Conversions

**False values:**

- number `0`
- empty string `""`
- `null`
- `undefined`
- `NaN`

**Truth values:**

- anything else aside from the above


---
# 02 - Variables


## Types

There are only 2 types of variables:

1. `let`
2. `const`
3. `var` (older version of `let`)

## Data Types

[More Info](https://javascript.info/types#:~:text=much%20more%20common.-,Summary,-There%20are%208)

| Type      - | Mutabiltity | Description                                                      x |
| ----------- | ----------- | ------------------------------------------------------------------ |
| number      | immutable   | integer(whole num) or floating point(decimal num)                  |
| bigint      | immutable   | 643116n  // n characterizes the number as bigint                   |
| string      | immutable   | "" , ''  are the same; `` is used for embedding variables          |
| boolean     | immutable   | true/false                                                         |
| null        | immutable   | represents "nothing", "empty", or "value unknown"                  |
| undefined   | immutable   | "value is not assigned"                                            |
| object      | mutable     | stores collections of data and more complex entities               |
| symbol      | immutable   | used to create unique identifiers for objects                      |


To check a variable's data type:

```js
typeof variableName;
```


## Null vs Undefined

Normally, one uses `null` to assign an “empty” or “unknown” value to a variable, while `undefined` is reserved as a default initial value for unassigned things.



---
# 03 - Strings


## Single vs Double vs Backtick Quotes

Single and double quotes function the same. They are used interchangeably but using both can be useful when the string content itself uses one of them. For example:

```js
let x = "Hello! I'm an example.";
let y = 'He said, "I\'m an example."'; // use '/' when it gets complex like in this example
```

Backtick quotes are used to embed a variable inside a string:

```js
let x = 10;
let y = `Use backticks like this to insert a variable: ${x}`;
```


## Convert data types into string

The function `String()` converts other data types into a string.


## Basic String Methods

Javascript strings are primitive and immutable. All string methods produce a new string without altering the original string.

| String Methods | -                                x |
| -------------- | ---------------------------------- |
| .length        | .isWellFormed()                    |
| .charAt()      | .toWellFormed()                    |
| .charCodeAt()  | .trim()                            |
| .codePointAt() | .trimStart()                       |
| .concat()      | .trimEnd()                         |
| .at()          | .padStart()                        |
| []             | .padEnd()                          |
| .slice()       | .repeat()                          |
| .substring()   | .replace()                         |
| .substr()      | .replaceAll()                      |
| .toUpperCase() | .split()                           |
| .toLowerCase() |                                    |

Other string methods:
https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String


If comparisons become tricky/confusing:
https://javascript.info/comparison

Checking for `null/undefined` separately is a good idea.


---
# 04 - Conditionals


## If...else syntax

```js
if (condition) {
  /* code to run if condition is true */
} else {
  /* run some other code instead */
}
```


## Connecting if...else statements to HTML:

```html
<label for="weather">Select the weather type today: </label>
<select id="weather">
  <option value="">--Make a choice--</option>
  <option value="sunny">Sunny</option>
  <option value="rainy">Rainy</option>
  <option value="snowing">Snowing</option>
  <option value="overcast">Overcast</option>
</select>

<p></p>
```

```js
const select = document.querySelector("select");
const para = document.querySelector("p");

select.addEventListener("change", setWeather);

function setWeather() {
  const choice = select.value;

  if (choice === "sunny") {
    para.textContent =
      "It is nice and sunny outside today. Wear shorts! Go to the beach, or the park, and get an ice cream.";
  } else if (choice === "rainy") {
    para.textContent =
      "Rain is falling outside; take a rain coat and an umbrella, and don't stay out for too long.";
  } else if (choice === "snowing") {
    para.textContent =
      "The snow is coming down — it is freezing! Best to stay in with a cup of hot chocolate, or go build a snowman.";
  } else if (choice === "overcast") {
    para.textContent =
      "It isn't raining, but the sky is grey and gloomy; it could turn any minute, so take a rain coat just in case.";
  } else {
    para.textContent = "";
  }
}
```


## Switch syntax:

```js
switch (expression) {
  case choice1:
    // run this code
    break;

  case choice2:
    // run this code instead
    break;

  // include as many cases as you like

  default:
    // actually, just run this code
    break;
}
```


## Connecting a switch statement to HTML:

```html
<label for="weather">Select the weather type today: </label>
<select id="weather">
  <option value="">--Make a choice--</option>
  <option value="sunny">Sunny</option>
  <option value="rainy">Rainy</option>
  <option value="snowing">Snowing</option>
  <option value="overcast">Overcast</option>
</select>

<p></p>
```

```js
const select = document.querySelector("select");
const para = document.querySelector("p");

select.addEventListener("change", setWeather);

function setWeather() {
  const choice = select.value;

  switch (choice) {
    case "sunny":
      para.textContent =
        "It is nice and sunny outside today. Wear shorts! Go to the beach, or the park, and get an ice cream.";
      break;
    case "rainy":
      para.textContent =
        "Rain is falling outside; take a rain coat and an umbrella, and don't stay out for too long.";
      break;
    case "snowing":
      para.textContent =
        "The snow is coming down — it is freezing! Best to stay in with a cup of hot chocolate, or go build a snowman.";
      break;
    case "overcast":
      para.textContent =
        "It isn't raining, but the sky is grey and gloomy; it could turn any minute, so take a rain coat just in case.";
      break;
    default:
      para.textContent = "";
  }
}
```


## Usage Advice

**Use switches when:**

- checking a variable against many exact values
- visual clarity and readability is prioritized
- using fall-through behavior (multiple cases, same result)


**Use if...else when:**

- conditions need ranges (<, <=, etc)
- conditions have many variables
- for complex boolean logic (&&, ||)
- simple 2-3 conditions


**If...else is more common** in modern JavaScript codebases because:

- It handles any condition type
- More flexible for complex logic
- Works with ranges and compound conditions

```js
// Switch: Good for specific values, readable
switch(x) { case 'a': return 1; }

// If-else: Good for complex conditions
if (x > 10 && y < 5) { return 1; }

// Object lookup: Best for simple key-value mappings
const map = {'a': 1, 'b': 2};
return map[x];
```


## Ternary/Question Mark Operator Syntax

```js
condition ? run this code : run this code instead
```

```js
const greeting = isBirthday
  ? "Happy birthday Mrs. Smith — we hope you have a great day!"
  : "Good morning Mrs. Smith.";
```

```js
// Use parentheses for better readability
let accessAllowed = (age > 18) ? true : false;
```

## Connecting ternary operators to HTML:

```html
<label for="theme">Select theme: </label>
<select id="theme">
  <option value="white">White</option>
  <option value="black">Black</option>
</select>

<h1>This is my website</h1>
```

```js
const select = document.querySelector("select");
const html = document.querySelector("html");
document.body.style.padding = "10px";

function update(bgColor, textColor) {
  html.style.backgroundColor = bgColor;
  html.style.color = textColor;
}

select.addEventListener("change", () =>
  select.value === "black"
    ? update("black", "white")
    : update("white", "black"),
);
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
https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String

### Comparisons
https://javascript.info/comparison
https://javascript.info/logical-operators

### Conditionals
https://developer.mozilla.org/en-US/docs/Learn_web_development/Core/Scripting/Conditionals
