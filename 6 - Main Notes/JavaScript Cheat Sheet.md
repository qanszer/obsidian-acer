
2025-10-21  13:28

Tags: [[JavaScript]], [[Coding]], [[The Odin Project]]

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
3. `var` (older version of `let`, should not be used)

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
# 05 - Functions


## Syntax

```javascript
function name(parameter1, parameter2, ... parameterN) {
	// code
}
```

```js
function showMessage() {
	alert( 'Hello everyone!' );
}
```


**Remember**: A variable declared inside a function is only visible inside that function. It cannot be called upon outside of the function.

**But** functions are able to use variables from the outside. It can even modify the variable inside the function.


## Global Variables

- Variables declared outside of any function are called _global_.
	
- Global variables are visible from any function (unless shadowed by locals).
	
- It’s a **good practice to minimize the use of global variables**. Modern code has few or no globals. Most variables reside in their functions. Sometimes though, they can be useful to store project-level data.

To make the code clean and easy to understand, it’s recommended to use mainly local variables and parameters in the function, not outer variables


## Default Values

If a function is called, but an argument is not provided, then the corresponding value becomes `undefined`. For example:

```js
function showMessage(from, text) {
	alert( from + ": " + text);
}

showMessage("Ann"); // Ann: undefined
```

We can use "default" values in the parameter to solve this.

```js
function showMessage(from, text = "no text given") {
	alert( from + ": " + text);
}

showMessage("Ann"); // Ann: no text given
```

This is also possible if it needs a more complex default value:

```js
function showMessage(from, text = anotherFunction() {
	alert( from + ": " + text);
}
```


## Naming a Function

Functions are actions. So their name is usually a verb. It should be brief, as accurate as possible and describe what the function does, so that someone reading the code gets an indication of what the function does.

It is a widespread practice to start a function with a verbal prefix which vaguely describes the action. **There must be an agreement within the team** on the meaning of the prefixes.

Example functions starting with…

- `"get…"` – return a value,
- `"calc…"` – calculate something,
- `"create…"` – create something,
- `"check…"` – check something and return a boolean, etc.

**Main Rule:** **One function -- one action**

A function should do exactly what is suggested by its name, no more.

Two independent actions usually deserve two functions, even if they are usually called together (in that case we can make a 3rd function that calls those two).

A few examples of breaking this rule:

- `getAge` – would be bad if it shows an `alert` with the age (should only get).
- `createForm` – would be bad if it modifies the document, adding a form to it (should only create it and return).
- `checkPermission` – would be bad if it displays the `access granted/denied` message (should only perform the check and return the result).

Functions should be short and do exactly one thing. If that thing is big, maybe it’s worth it to split the function into a few smaller functions. Sometimes **following this rule may not be that easy**, but it’s definitely a good thing.


The first variant uses a label:

```javascript
function showPrimes(n) {
  nextPrime: for (let i = 2; i < n; i++) {

    for (let j = 2; j < i; j++) {
      if (i % j == 0) continue nextPrime;
    }

    alert( i ); // a prime
  }
}
```

The second variant uses an additional function `isPrime(n)` to test for primality:

```javascript
function showPrimes(n) {

  for (let i = 2; i < n; i++) {
    if (!isPrime(i)) continue;

    alert(i);  // a prime
  }
}

function isPrime(n) {
  for (let i = 2; i < n; i++) {
    if ( n % i == 0) return false;
  }
  return true;
}
```

The second variant is easier to understand, isn’t it? **Instead of the code piece we see a name of the action (`isPrime`)**. Sometimes people refer to such code as _self-describing_.

So, **functions can be created even if we don’t intend to reuse them**. They structure the code and make it readable.


## Scopes

[More info](https://developer.mozilla.org/en-US/docs/Learn_web_development/Core/Scripting/Functions#function_scope_and_conflicts)

When we create functions, the code blocks inside them are half-separate from the outside code. Half-separate, because **variables outside of the function can be called and used** (global scopes), but **variables inside the function *cannot* be called and cannot be used outside of the function** (function scopes).

If made with an analogy of a zoo, the functions themselves are areas for each type of animal's environment---jungle, snow, savannah, etc. 

If a variable (lion) from one function (savannah) is called from another function (snow), it would not happen and would result in an error.

Javascript works like this mainly for security and organization.

**Reminder:** The `ReferenceError: "x" is not defined` error is one of the most common you'll encounter. If you get this error and you are sure that you have defined the variable in question, check what scope it is in.


**Loops** (while, for) and **conditionals** (if, if else) **also apply** to this. **They also have their own scopes**. That means the variables that are declared inside of them cannot be accessed to the outside blocks of code.


## Return Values

Generally, a return value is **used where the function is an intermediate step in a calculation of some kind**. You want to get to a final result, which involves some values that need to be calculated by a function.

After the function calculates the value, it can return the result so it can be stored in a variable; and you can use this variable in the next stage of the calculation.


## Function Expressions
[More info](https://javascript.info/function-expressions)

**Callback Functions**
[More info](https://javascript.info/function-expressions#callback-functions)


## Arrow Functions
[More info](https://javascript.info/arrow-functions-basics)

The functions `map()` and `filter()` are often used with function expressions

```js
const cats = ["Leopard", "Serval", "Jaguar", "Tiger", "Caracal", "Lion"];

const filtered = cats.filter((cat) => cat.startsWith("L"));
console.log(filtered);
// [ "Leopard", "Lion" ]
```


---
# 06 - Loops


## Syntax

```js
// for loop
for (initializer; condition; final-expression) {
  // code to run
}
```

```js
// while loop
initializer
while (condition) {
  // code to run

  final-expression
}
```

```js
// do...while loop
initializer
do {
  // code to run

  final-expression
} while (condition)
```


## Two ways of using loops for collections

```js
// Method 1 - Standard Practice
const cats = ["Leopard", "Serval", "Jaguar", "Tiger", "Caracal", "Lion"]; 

for (const cat of cats) {
	console.log(cat);
}
```

```js
// Method 2 - Classic For Loop
const cats = ["Leopard", "Serval", "Jaguar", "Tiger", "Caracal", "Lion"];

for (let i = 0; i < cats.length; i++) {
  console.log(cats[i]);
}
```

**Reminders for the classic `for` loop:**
1. The counter variable `i` should always start at `0` because the first index of an array is 0, not 1.
2. The last array index is at `length - 1`, so `i <= cats.length` is incorrect.


**Tip:** Only use the classic `for` loop when an iteration in the loop should differ from the rest. Like here:

```js
const cats = ["Pete", "Biggles", "Jasmine"];

let myFavoriteCats = "My cats are called ";

for (const cat of cats) {
  myFavoriteCats += `${cat}, `;
}

console.log(myFavoriteCats); // "My cats are called Pete, Biggles, Jasmine, "
```

The final output sentence isn't very well-formed:

```
My cats are called Pete, Biggles, Jasmine,
```

We'd prefer it to handle the last cat differently, like this:

```
My cats are called Pete, Biggles, and Jasmine.
```

But to do this we need to know when we are on the final loop iteration, and to do that we can use a `for` loop and examine the value of `i`:

```js
const cats = ["Pete", "Biggles", "Jasmine"];

let myFavoriteCats = "My cats are called ";

for (let i = 0; i < cats.length; i++) {
  if (i === cats.length - 1) {
    // We are at the end of the array
    myFavoriteCats += `and ${cats[i]}.`;
  } else {
    myFavoriteCats += `${cats[i]}, `;
  }
}

console.log(myFavoriteCats); // "My cats are called Pete, Biggles, and Jasmine."
```


## Break Statement
[More info](https://developer.mozilla.org/en-US/docs/Learn_web_development/Core/Scripting/Loops#exiting_loops_with_break)

A `break` statement will immediately exit the loop and make the browser move on to any code that follows it.

Say we wanted to search through an array of contacts and telephone numbers and return just the number we wanted to find? We can use the `break` statement.

## Continue Statement
[More info](https://developer.mozilla.org/en-US/docs/Learn_web_development/Core/Scripting/Loops#skipping_iterations_with_continue)

A `continue` statement skips to the next iteration of the loop.


## Labels

`break/continue` support labels before the loop. A label is the only way for `break/continue` to escape a nested loop to go to an outer one.

```js
outer: for (let i = 0; i < 3; i++) {

	for (let j = 0; j < 3; j++) {
		let input = prompt(`Value at coords (${i}, ${j})`, '');
		
		// if an empty string or canceled, then break out of both loops
		if (!input) break outer; // (*)
		
		// do something with the value
	}
}

alert(`Done!);
```


## MDN Playground Exercise
[Try it yourself](https://developer.mozilla.org/en-US/play?uuid=3504afee6ad46a0bc42f2162b4f26f1c06bc0474&state=fVJNj9MwEP0ro0FIINq0ReJjnabS0iMcEMsNc3CTSWPWsYM96W5Z7X9fOR8GlhW3eeP33oztd4cNtwYFbit9gtKoEAqJrueuZ4k7aQG2XeqrqtXMVEncXcZSbFfdY46nug8D5ctQTZztqtKnnbS4wDIEFMNcuIvi2lle1qrV5iwgKBuWgbyuc2nvpZW2ef0HLehfJGDztrudjzO12ZyXRh1osmuVP2orYJ1HxHTLS2X00Qrw%2Bthw%2Fshrnb3z1A7dG11xI%2BDi%2FfPZ%2FOCq89%2Bum%2FUwGuCgyuujd72tBDyr39QXtUorje83ChuKU6NwVroT%2Bdq4GwGqZzeKcIE%2F4quUzgaGjlxnCAr4FvkS943XQeJiRJfWUgJ7Z7RN6Ct5rxP63GiTwCdnVAJXqk31R3VO9Qffl6P39zzeZFxn%2FnYooHJl35Ll7GdP%2FnxFhkp2%2FoXE7Hc2XuazcMrCf3UpL1E2m2Tx2%2FbOMlmGIt55iBtIzKWdFP9wpryNJGlXKzDOdRBYeQ7QkKep%2FZTBqwKyLMuH8ye3SARcIDfUEgqslL%2FG%2Bwc%3D&srcPrefix=%2Fen-US%2Fdocs%2FLearn_web_development%2FCore%2FScripting%2FLoops%2F)

Display the contents of a collection/array while making the last part not a comma, but a period:

```js
// My attempt - bad and rough
const people = [
  "Chris",
  "Anne",
  "Colin",
  "Terri",
  "Phil",
  "Lola",
  "Sam",
  "Kay",
  "Bruce",
];

const admitted = document.querySelector(".admitted");
const refused = document.querySelector(".refused");
admitted.textContent = "Admit: ";
refused.textContent = "Refuse: ";


for (let i = 0; i < people.length; i++) {
  if (i === people.length - 1) {
    admitted.textContent += `${people[i]}.`;
  }
  else {
    if (people[i] === "Phil") {
      refused.textContent += `${people[i]}, `;
      continue;
    }
    if (people[i] === "Lola") {
      refused.textContent += `${people[i]}.`;
      continue;
    }
    admitted.textContent += `${people[i]}, `;
  }
}

// Output
// Admit: Chris, Anne, Colin, Terri, Sam, Kay, Bruce.
// Refuse: Phil, Lola.
```

```js
// The correct answer - clean and alot better
const people = [
  "Chris",
  "Anne",
  "Colin",
  "Terri",
  "Phil",
  "Lola",
  "Sam",
  "Kay",
  "Bruce",
];

const admitted = document.querySelector(".admitted");
const refused = document.querySelector(".refused");
admitted.textContent = "Admit: ";
refused.textContent = "Refuse: ";

for (const person of people) {
  if (person === "Phil" || person === "Lola") {
    refused.textContent += `${person}, `;
  } else {
    admitted.textContent += `${person}, `;
  }
}

refused.textContent = `${refused.textContent.slice(0, -2)}.`;
admitted.textContent = `${admitted.textContent.slice(0, -2)}.`;

// Output
// Admit: Chris, Anne, Colin, Terri, Sam, Kay, Bruce.
// Refuse: Phil, Lola.
```


## Which loops to use for each usecase?

If you're iterating through an array or some other object that supports it, and don't need access to the index position of each item, then `for...of` is the best choice. It's easier to read and there's less to go wrong.

For other uses, `for`, `while`, and `do...while` loops are largely interchangeable. They can all be used to solve the same problems, and which one you use will largely depend on your personal preference — which one you find easiest to remember or most intuitive. We would recommend `for`, at least to begin with, as it is probably the easiest for remembering everything — the initializer, condition, and final-expression all have to go neatly into the parentheses, so it is easy to see where they are and check that you aren't missing them.

One use of `do...while` is when you want the user to input something until they get it right:

```js
let input;

do {
input = prompt("Type a number greater than 100");
} while (input < 100 && input);
```


---
# 07 - Arrays

Arrays in JavaScript are **dynamic** -- their size can be changed and are not immutable like in C or Java. Elements inside arrays can be added, removed, and changed freely.

They are suited for storing and managing ordered data items.

## Syntax

```js
let arr = new Array(); // avoid using this in javascript
let arr = []; // used 99% of the time; the usual
```

They can store elements of any type:

```js
let arr = [ 'Apple',               // string
	{ name: 'John' },              // object
	true,                          // boolean
	function() { alert('hello'); } // function
];

// get the object at index 1 and then show its name
alert( arr[1].name ); // John

// get the function at index 3 and run it
arr[3](); // hello
```


## Trailing Comma

This style makes it easier to insert/remove items because all lines become alike

```js
let fruits = [
	"apple",
	"orange",
	"banana",
]
```


## Negative indexes

For getting the last element of the array, some programming languages use negative indexes like `fruits[-1]`, but it won't work in JavaScript.

JavaScript's solution is `fruits.at(-1)`

`arr.at(i)`
- exactly the same as `arr[i]` which is the standard syntax for most programming languages


## Queues/Stacks

**Queue**
- operations:
	- `push` adds an element to the end
	- `shift` gets an element from the beginning, making the 2nd element become 1st
- FIFO (first in first out)

![[Pasted image 20260323203739.png]]

**Stack**
- operations:
	- `push` adds an element to the end
	- `pop` takes an element from the end
- LIFO (last in first out)
- usually described as a stack of cards on top of each other

![[Pasted image 20260323203942.png]]


**Methods** that work with the **end** of the array:

1. `pop` - removes the last element of the array and returns it
```js
alert( fruits.pop() );
```

2. `push` - adds the element to the end of the array
```js
fruits.push("Pear", "Lemon"); // can have multiple elements
```

**Methods** that work with the **beginning** of the array:

1. `shift` - removes the 1st element of the array and returns it
```js
fruits.shift();
```

2. `unshift` - adds the element to the beginning of the array
```js
alert( fruits.unshift("Apple", "Pineapple") ); // can have multiple values
```


## Array Specifics

An array is a special kind of object. The square brackets used to access a property `arr[0]` actually come from the object syntax. That’s essentially the same as `obj[key]`, where `arr` is the object, while numbers are used as keys.

They extend objects providing special methods to work with ordered collections of data and also the `length` property. But at the core it’s still an object.

Remember, there are only eight basic data types in JavaScript (see the [Data types](https://javascript.info/types) chapter for more info). Array is an object and thus behaves like an object.


**Copies of arrays are only by reference**, not a completely separate array:

```js
let fruits = ["banana"];
let arr = fruits; // copy by reference (2 variables are now holding the same array)

alert(arr === fruits); // true

arr.push("pear"); // if you modify the new array variable (arr),

alert(fruits); // the original array variable also gets updated
```


## The ways to misuse an array

- Add a non-numeric property like `arr.test = 5`.
- Make holes, like: add `arr[0]` and then `arr[1000]` (and nothing between them).
- Fill the array in the reverse order, like `arr[1000]`, `arr[999]` and so on.

Please think of arrays as special structures to work with the _ordered data_. They provide special methods for that. Arrays are carefully tuned inside JavaScript engines to work with contiguous ordered data, please use them this way. And if you need arbitrary keys, chances are high that you actually require a regular object `{}`.


## Performance
[More info](https://javascript.info/array#performance)

Methods `push/pop` run fast, while `shift/unshift` are slow.

![[Pasted image 20260323212422.png]]


## Loops for arrays

**2 Methods**:

```js
// classic for loop
for (let i = 0; i < arr.length; i++) {
	alert(arr[i]);
}
```

```js
// better loop for arrays, the for...of loop
for (let fruit of fruits) {
	alert(fruit);
}
```

The `for..of` doesn’t give access to the number of the current element, just its value, but in most cases that’s enough. And it’s shorter.

Reason as to why `for...in` loops are bad for arrays: [Link](https://javascript.info/array#internals:~:text=And%20it%E2%80%99s%20shorter.-,Technically,-%2C%20because%20arrays%20are)

So to loop over the elements of the array:

- `for (let i=0; i<arr.length; i++)` – works fastest, old-browser-compatible.
- `for (let item of arr)` – the modern syntax for items only. shorter and more readable.
- `for (let i in arr)` – never use.


## Clear the array

Remove all the elements of an array while keeping the array itself:

```js
arr.length = 0;
```


## About String(array)

In JavaScript, `String(arr)` and printing the array as-is (`console.log(arr)`) often appear to produce the same result because both trigger the array's default `toString()` method, which converts the array into a comma-separated string.

However, the purpose of explicitly using `String(arr)` is to **coerce the array into a primitive string type for manipulation, concatenation, or storage**, rather than just displaying it. 

**KEY PURPOSES OF `String(arr)`**

1. **Guaranteed Type Conversion (Coercion):**  
    `String(arr)` ensures the result is a string primitive, which is useful when you need to concatenate the array contents with text or pass it to a function that requires a string.

```js
let arr = [1, 2, 3];
let message = "Result: " + String(arr); // "Result: 1,2,3"
```

2. **Flattening Nested Arrays:**  
    The `String()` constructor (like `.toString()`) recursively flattens arrays, converting all elements to strings separated by commas, including nested arrays.

```js
String([1, [2, 3], 4]); // "1,2,3,4"
```

3. **Handling `null` or `undefined` Safely:**  
    If `arr` might be `null` or `undefined`, `String(arr)` safely returns `"null"` or `"undefined"` without throwing an error, whereas calling `arr.toString()` on them would throw a `TypeError`. 

**Note on Behavior**:

`String(arr)` internally calls `arr.toString()`, which in turn calls `arr.join(",")`. Therefore, it effectively creates a string where all items are comma-delimited, without square brackets `[]`.


## String Concatenation

```js
alert( [] + 1 ); // "1"
alert( [1] + 1 ); // "11"
alert( [1,2] + 1 ); // "1,21"
```

Arrays do not have `Symbol.toPrimitive`, neither a viable `valueOf`, they implement only `toString` conversion, so here `[]` becomes an empty string, `[1]` becomes `"1"` and `[1,2]` becomes `"1,2"`.


## Don't compare arrrays with ==

The strict comparison `===` is even simpler, as it doesn’t convert types.

So, if we compare arrays with `==`, they are never the same, unless we compare two variables that reference exactly the same array.

So, how to compare arrays? 
Don’t use the `==` operator. Instead, compare them item-by-item in a loop or using iteration methods.

## Array Methods

Negative indexes are allowed in many array methods.

**`arr.splice`**

This method can insert, remove, and replace elements

```js
// syntax
arr.splice(start[, deleteCount, elem1, ..., elemN])
```

```js
// remove
let arr = ["I", "study", "javascript"];
arr.splice(1,1); // from index 1, remove 1 element
alert(arr); // ["I", "javascript"]
```

```js
// replace
arr.splice(2, 1, "java", "and c#"); // from index 2, remove 1 element and replace with java and c#
```

```js
// check what you removed
let arr = ["I", "study", "javascript", "right", "now"];
let removed = arr.splice(0,2); // removes first 2 elements
alert(removed); // "I", "study"
```

```js
// insert elements
let arr = ["I", "study", "javascript"];
arr.splice(2, 0, "complex", "language"); // from index 2, delete none, insert "complex" and "language"
alert(arr); // 
```


**`arr.slice`**

This **method copies the array and makes it a separate array**, unlike copying through reference.




---
# References


### Main Reference - The Odin Project
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

### Functions
https://javascript.info/function-basics
https://developer.mozilla.org/en-US/docs/Learn_web_development/Core/Scripting/Functions
https://developer.mozilla.org/en-US/docs/Learn_web_development/Core/Scripting/Return_values
https://javascript.info/function-expressions
https://javascript.info/arrow-functions-basics