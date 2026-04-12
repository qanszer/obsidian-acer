
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

**Boolean methods to check a variable's datatype**

- int: `Number.isInteger(variable)`
- string: `typeof variable === 'string'`
- array: `Array.isArray(variable)`


**Method for checking if a variable has that specific variable/value:**

- `.includes(element/variable/value)`


## Rounding off

Custom function:
```js
function roundTo(num, precision) {
  if (precision === undefined || precision === null) return Math.round(num); // Handle default integer rounding
  // Convert to exponential notation, round, and convert back
  return Number(Math.round(num + "e+" + precision) + "e-" + precision);
}
```

Round to 1 decimal point:
```js
Math.round(celsius * 10) / 10;
```


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


## Random Functions

For random negative/positive return:
```js
() => Math.random() > 0.5 ? 1 : -1
```

For random whole number between 1-100:
```js
() => Math.floor(Math.random() * 100) + 1
```


## Callbacks

Put simply, **callbacks are functions** that are passed into another function as an argument.

You most likely have seen, or even used, callbacks and not realized it. They are used frequently in JavaScript. **Understanding JavaScript is impossible without understanding callbacks**. Below is an example of something you may have run into before.

```js
const notes = ['do', 're', 'me'];

notes.forEach((note) => console.log(note));
```

This is the `forEach` array method. This method simply takes a `callback` function as its argument.


**How Callbacks Work**

To state it once more: **Callbacks are just functions** passed into other functions as arguments (as a parameter).


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

#### > Add/Remove Items

**0. `arr.push()`**

This method adds the inputted elements to an array.

```js
arr.push(item, 3, "e");
```

**1. `arr.splice()`** - returns a new modified array, and modifies the original array

This method can insert, remove, and replace elements.

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

```js
// negative indexes are allowed in array methods
let arr = [1, 2, 5];

// from index -1 (one step from the end)
// delete 0 elements,
// then insert 3 and 4
arr.splice(-1, 0, 3, 4);

alert( arr ); // 1,2,3,4,5
```

**2. `arr.slice()`** - returns a new array; does not affect the original array

This **method copies the array and makes it a separate array**, unlike copying through reference.

```js
let arr = ["t", "e", "s", "t"];

// starts at 1
// ends at 3 (excluding index 3)
alert( arr.slice(1, 3) ); // e,s (copy from 1 to 3)
alert( arr.slice(-2) ); // s,t (copy from -2 till the end)
arr.slice(); // copies the entire array. used for further transformations that should not affect the original array
```

**3. `arr.concat()`** - returns a new array; does not affect the original array

This method creates a new array that includes values from other arrays and additional items.

```js
let arr = [1, 2];

// create an array from: arr and [3,4]
alert( arr.concat([3, 4]) ); // 1,2,3,4

// create an array from: arr and [3,4], then add values 5 and 6
alert( arr.concat([3, 4], 5, 6) ); // 1,2,3,4,5,6
```

[Symbol.isConcatSpreadable](https://javascript.info/array-methods#searching-in-array:~:text=has%20a%20special-,Symbol.isConcatSpreadable,-property%2C%20then%20it%E2%80%99s) - object property that treats objects as arrays

**4. `arr.forEach()`** - no return value; a loop; for performing a specific action for each item

This method allows to run a function for every element of the array.

```js
// syntax
arr.forEach(function(item, index, array){
	// do something with an item
});
```

```js
// for each element call alert
["Bilbo", "Gandalf", "Nazgul"].forEach(alert);

["Bilbo", "Gandalf", "Nazgul"].forEach((item, index, array) => {
	alert(`${item} is at index ${index} in ${array}`);
});
```


#### > Searching in Arrays

**1. `arr.indexOf(item, from)`** - returns an index

This method looks for `item` starting from index `from`, and then returns the index where `item` was found. If not found, it would return `-1`.

```js
let arr = [1, 0, false];

// you input the item itself on the parameter, not its index
alert( arr.indexOf(0) ); // 1
alert( arr.indexOf(false) ); // 2
alert( arr.indexOf(5) ); // -1
```

**2. `arr.includes(item, from)`** - returns a boolean; checks if the item exists

```js
// array based above
alert( arr.includes(1) ); // true
```

**3. `arr.lastIndexOf(item, from)`** - returns a boolean

This method is the same as `indexOf`, but looks from right to left.

```js
let fruits = ['Apple', 'Orange', 'Apple']

alert( fruits.indexOf('Apple') ); // 0 (first Apple)
alert( fruits.lastIndexOf('Apple') ); // 2 (last Apple)
```

The `includes` method handles `NaN` correctly. [Link](https://javascript.info/array-methods#searching-in-array:~:text=2%20(last%20Apple)-,The,-includes%20method%20handles)

**4. `find` and `findIndex/findLastIndex`** - [details](https://javascript.info/array-methods#find-and-findindex-findlastindex)

```js
// syntax
let result = arr.find(function(item, index, array) {
	
})
```

```js
// example
let users = [
	{id: 1, name: "John"},
	{id: 2, name: "Pete"},
	{id: 3, name: "Mary"}
];

let user = users.find(item => item.id == 1);

alert(user.name); // John
```
In real life, arrays of objects are a common thing, so the `find` method is very useful.

Note that in the example we provide to `find` the function `item => item.id == 1` with one argument. That’s typical, other arguments of this function are rarely used.

The [arr.findIndex](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/findIndex) method has the same syntax but returns the index where the element was found instead of the element itself. The value of `-1` is returned if nothing is found.

The [arr.findLastIndex](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/findLastIndex) method is like `findIndex`, but searches from right to left, similar to `lastIndexOf`.

```js
let users = [
	{id: 1, name: "John"},
	{id: 2, name: "Pete"},
	{id: 3, name: "Mary"},
	{id: 4, name: "John"}
];

// Find the index of the first John
alert(users.findIndex(user => user.name == 'John')); // 0

// Find the index of the last John
alert(users.findLastIndex(user => user.name == 'John')); // 3
```

**5. `filter`** 

The `find` method looks for a single (first) element that makes the function return `true`.

If there may be many, we can use `arr.filter(fn)`.

```js
// syntax
let results = arr.filter(function(item, index, array) {
	
})
```

```js
let users = [
	{id: 1, name: "John"},
	{id: 2, name: "Pete"},
	{id: 3, name: "Mary"}
];

// returns array of the first two users
let someUsers = users.filter(item => item.id < 3);

alert(someUsers.length); // 2
```


#### > Transform/Reorder an Array

**1. `arr.map()`** - returns the array of results

This method is one of the most useful and often used.
**Usecase** - when we need to iterate and return the data for each element

```js
// syntax
let result = arr.map(function(item, index, array) {
	
})
```

```js
// example
let lengths = ["Bilbo", "Gandalf", "Nazgul"].map(item => item.length);

alert(lengths); // 5,7,6
```

**2. `arr.sort()`**
[More info](https://javascript.info/array-methods#searching-in-array:~:text=it%20works%20as-,intended.,-Let%E2%80%99s%20step%20aside)

This method sorts the array _in place_, changing its element order.

The items are sorted as strings by default, so we need to supply a function as the argument.

The function should compare two arbitrary values and return:

```js
function compare(a, b) {
	if (a > b) return 1; // if the 1st value is greater than the 2nd
	if (a == b) return 0; // if values are equal
	if (a < b) return -1; // if the 1st value is less than the 2nd
}
```

For instance, to sort as numbers:

```js
let arr = [ 1, 2, 15 ];

arr.sort((a, b) => a - b); // increasing order

alert(arr); // 1, 2, 15
```

**For copy-paste**:

```js
.sort((a, b) => a - b); // increasing order
```

```js
.sort((a, b) => b - a); // decreasing order
```

```js
.sort((a, b) => a.localeCompare(b)); // alphabetical
```

**3. `arr.reverse()`** - returns the modified original array

This method reverses the order of elements in the array.

```js
let arr = [1, 2, 3, 4, 5];
arr.reverse();

alert( arr ); // 5,4,3,2,1
```

**4. `string.split(', ')`**

This method splits the string into an array by the given delimiter inside the parameter.

```js
let names = 'Bilbo, Gandalf, Nazgul';

let arr = names.split(', ');

for (let name of arr) {
	// A message to Bilbo (and other names)
	alert( `A message to ${name}.` );
}
```

Calling `.split('')` with an empty parameter splits the string into an array of letters:

```js
let str = "test";
alert( str.split('') ); // t,e,s,t
```

**5. `arr.join(glue)`**

This method does the reverse to `split`. It creates a string of `arr` items joined by `glue` between them.

```js
let arr = ['Bilbo', 'Gandalf', 'Nazgul'];

let str = arr.join(';'); // glue the array into a string using ;
alert( str ); // Bilbo;Gandalf;Nazgul
```

**6. `arr.reduce()` and `arr.reduceRight()`** - [more info](https://javascript.info/array-methods#reduce-reduceright)

These methods are used to calculate a single value based on the array.

```js
// syntax
let value = arr.reduce(function(accumulator, item, index, array) {
	
}, [initial]); 
```

The function is applied to all array elements one after another and “carries on” its result to the next call.

Arguments:
- `accumulator` – is the result of the previous function call, equals `initial` the first time (if `initial` is provided).
- `item` – is the current array item.
- `index` – is its position.
- `array` – is the array.

```js
// example
let arr = [1, 2, 3, 4, 5];

let result = arr.reduce((sum, current) => sum + current, 0);
alert(result); // 15
```

The function passed to `reduce` uses only 2 arguments, that’s typically enough.

I don't get this. For more info, [click here](https://javascript.info/array-methods#reduce-reduceright).


## Array.isArray

`typeof` does not help to distinguish a plain object from an array:

```js
alert(typeof {}); // object
alert(typeof []); // object (same)
```

But arrays are used so often that there’s a special method for that:

```js
alert(Array.isArray({})); // false
alert(Array.isArray([])); // true
```

## thisArg
[More info](https://javascript.info/array-methods#most-methods-support-thisarg)


## Summary/Cheatsheet

A cheat sheet of array methods:

- To add/remove elements:
    
    - `push(...items)` – adds items to the end,
    - `pop()` – extracts an item from the end,
    - `shift()` – extracts an item from the beginning,
    - `unshift(...items)` – adds items to the beginning.
    - `splice(pos, deleteCount, ...items)` – at index `pos` deletes `deleteCount` elements and inserts `items`.
    - `slice(start, end)` – creates a new array, copies elements from index `start` till `end` (not inclusive) into it.
    - `concat(...items)` – returns a new array: copies all members of the current one and adds `items` to it. If any of `items` is an array, then its elements are taken.
- To search among elements:
    
    - `indexOf/lastIndexOf(item, pos)` – look for `item` starting from position `pos`, and return the index or `-1` if not found.
    - `includes(value)` – returns `true` if the array has `value`, otherwise `false`.
    - `find/filter(func)` – filter elements through the function, return first/all values that make it return `true`.
    - `findIndex` is like `find`, but returns the index instead of a value.
- To iterate over elements:
    
    - `forEach(func)` – calls `func` for every element, does not return anything.
- To transform the array:
    
    - `map(func)` – creates a new array from results of calling `func` for every element.
    - `sort(func)` – sorts the array in-place, then returns it.
    - `reverse()` – reverses the array in-place, then returns it.
    - `split/join` – convert a string to array and back.
    - `reduce/reduceRight(func, initial)` – calculate a single value over the array by calling `func` for each element and passing an intermediate result between the calls.
- Additionally:
    
    - `Array.isArray(value)` checks `value` for being an array, if so returns `true`, otherwise `false`.

Please note that methods `sort`, `reverse` and `splice` modify the array itself.

These methods are the most used ones, they cover 99% of use cases. But there are few others:

- [arr.some(fn)](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/some)/[arr.every(fn)](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/every) check the array.
    
    The function `fn` is called on each element of the array similar to `map`. If any/all results are `true`, returns `true`, otherwise `false`.
    
    These methods behave sort of like `||` and `&&` operators: if `fn` returns a truthy value, `arr.some()` immediately returns `true` and stops iterating over the rest of items; if `fn` returns a falsy value, `arr.every()` immediately returns `false` and stops iterating over the rest of items as well.
    
    We can use `every` to compare arrays:
```js
function arraysEqual(arr1, arr2) {
	return arr1.length === arr2.length && arr1.every((value, index) => value === arr2[index]);
}

alert( arraysEqual([1, 2], [1, 2])); // true
```
- [arr.fill(value, start, end)](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/fill) – fills the array with repeating `value` from index `start` to `end`.
    
- [arr.copyWithin(target, start, end)](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/copyWithin) – copies its elements from position `start` till position `end` into _itself_, at position `target` (overwrites existing).
    
- [arr.flat(depth)](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/flat)/[arr.flatMap(fn)](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/flatMap) create a new flat array from a multidimensional array.

## MDN's Official Array Documentation
[Link](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array)


## The Map Method

This method automatically loops over an array if you'll only use a function inside a loop. So it's **a simplified loop if you want to modify arrays**.

```js
// syntax
arr.map();
```

```js
// example
function addOne(num) {
  return num + 1;
}
const arr = [1, 2, 3, 4, 5];
const mappedArr = arr.map(addOne); // returns a new separate array
console.log(mappedArr); // Outputs [2, 3, 4, 5, 6]
```

We can simplify the code above like this through arrow functions:

```js
const arr = [1, 2, 3, 4, 5];
const mappedArr = arr.map((num) => num + 1);
console.log(mappedArr); // Outputs [2, 3, 4, 5, 6]
```

The `.map()` is always used with arrow functions usually because they pair well together.

## The Filter Method

By its name it filters out the array you use it on, by using your given function that returns a boolean (true or false). It returns a new array where each item is only included _if_ the callback function returns `true` for it.

```js
// syntax
arr.filter();
```

```js
// example
function isOdd(num) {
  return num % 2 !== 0;
}
const arr = [1, 2, 3, 4, 5];
const oddNums = arr.filter(isOdd);
console.log(oddNums); // Outputs [1, 3, 5];
console.log(arr); // Outputs [1, 2, 3, 4, 5], original array is not affected
```

## The Reduce Method

This method is that it will go through every element in `arr` and apply the `callback` function to it. It updates the `accumulator` withou actually changing the array itself. After it's done, it returns the `accumulator`.

```js
// rough syntax
arr.reduce((result, function) => {
	return result;
}, resultInitialValue);
```

```js
// example
const arr = [1, 2, 3, 4, 5];
const productOfAllNums = arr.reduce((total, currentItem) => {
  return total * currentItem;
}, 1);
console.log(productOfAllNums); // Outputs 120;
console.log(arr); // Outputs [1, 2, 3, 4, 5]
```

| **Visualization on the difference between the 3 methods:** |
| ---------------------------------------------------------- |
| ![[Pasted image 20260325213429.png]]                       |

## Consecutive Usage of Array Methods

```js
// the methods can be lined up like this
function sumOfTripledEvens(array) {
  return array
    .filter((num) => num % 2 === 0)
    .map((num) => num * 3)
    .reduce((acc, curr) => acc + curr);
}
```


## Shuffling an Array

**01 - The Fisher-Yates (aka Knuth) Shuffle** - use for large arrays of more than a few hundred

```js
function shuffle(array) {
	for (let i = array.length - 1; i > 0; i--) {
		let j = Math.floor(Math.random() * (i + 1));
		[array[i], array[j]] = [array[j], array[i]];
	}
}
```

**02 - Schwartzian Transform Shuffle** - use for arrays with less than a few hundred items

```js
// Source - https://stackoverflow.com/a/46545530
// Posted by superluminary, modified by community. See post 'Timeline' for change history
// Retrieved 2026-03-26, License - CC BY-SA 4.0
function shuffle(unshuffled) {
	return unshuffled
		.map(value => ({ value, sort: Math.random() }))
	    .sort((a, b) => a.sort - b.sort)
	    .map(({ value }) => value);
}
```



---
# 08 - Events


## Methods to Select HTML Elements

1. `querySelector()`
2. `getElementById()`

## Mouse Events
[More info](https://www.javascripttutorial.net/javascript-dom/javascript-mouse-events/)

1. `mousedown` - press the mouse button on the element
2. `mouseup` - release the mouse button on the element
3. `click` - one `mousedown` and one `mouseup` detected on the element
4. `dblclick` - 2 `click` events
5. `mousemove` - move the mouse cursor around an element
6. `mouseover` - pointer enters the element or any of its children; bubbles
7. `mouseout` - pointer leaves the element or any of its children; bubbles
8. `mouseenter` - pointer enters the element itself only; does not bubble
9. `mouseleave` - pointer leaves the element itself only; does not bubble
10. `wheel` - scroll the mouse wheel or touchpad

#### Select a mouse event

1. General - `addEventListener('click')`
2. Specific - `onclick`

**It’s a good practice to use the `addEventListener()` to register a mouse event handler.**

#### Mousemove

The `mousemove` event fires repeatedly whenever you move the mouse cursor around an element. This `mousemove` event fires many times per second as the mouse is moved around, even if it is just by one pixel. This may lead to a performance issue if the event handler function is complex.

To avoid the performance issue, it is a good practice to add `mousemove` event handler only when you need it and remove it as soon as it is no longer needed, like this:

```js
element.onmousemove = mouseMoveEventHandler;
// ...
//  later, no longer use
element.onmousemove = null;
```

#### Detecting mouse buttons

The `event` object passed to the mouse event handler has a property called `button` that indicates which mouse button was pressed on the mouse to trigger the event.

The mouse button is represented by a number:

- `0`: the main mouse button is pressed, usually the left button.
- `1`: the auxiliary button is pressed, usually the middle button or the wheel button.
- `2`: the secondary button is pressed, usually the right button.
- `3`: the fourth button is pressed, usually the Browser Back button.
- `4`: the fifth button is pressed, usually the _Browser Forward_ button.

![[Pasted image 20260406210502.png]]

```js
// example

btn.addEventListener('mouseup', (e) => {
	let msg = document.querySelector('#message');
	switch (e.button) {
		case 0:
			msg.textContent = 'Left mouse button clicked.';
			break;
		case 1:
			msg.textContent = 'Middle mouse button clicked.';
			break;
		case 2:
			msg.textContent = 'Right mouse button clicked.';
			break;
		default:
			msg.textContent = `Unknown mouse button code: ${event.button}`;
	}
});
```

#### Modifier keys

```js
.shiftKey
.ctrlKey
.altKey
.metaKey
```

When you click an element, you may press one or more modifier keys: Shift, Ctrl, Alt, and Meta. Note the Meta key is the Windows key on Windows keyboards and the Command key on the Apple keyboard.

To detect if these modifier keys have been pressed, you can use the `event` object passed to the mouse event handler.

The `event` object has four Boolean properties, where each is set to `true` if the key is being held down or `false` if the key is not pressed.

```js
// example

btnKeys.addEventListener('click', (e) => {
	let keys = [];

	if (e.shiftKey) keys.push('shift');
	if (e.ctrlKey) keys.push('ctrl');
	if (e.altKey) keys.push('alt');
	if (e.metaKey) keys.push('meta');

	let msg = document.querySelector('#messageKeys');
	msg.textContent = `Keys: ${keys.join('+')}`;
});
```

#### Bubbling behavior summary

|Event|Bubbles|Fires on child elements|
|---|---|---|
|mouseover|Yes|Yes|
|mouseout|Yes|Yes|
|mouseenter|No|No|
|mouseleave|No|No|
|click|Yes|N/A|
|dblclick|Yes|N/A|
|mousedown|Yes|N/A|
|mouseup|Yes|N/A|
|mousemove|Yes|N/A|
|wheel|Yes|N/A|

## Keyboard Events
[More info](https://www.javascripttutorial.net/javascript-dom/javascript-keyboard-events/)

1. `keydown` - press a key on the keyboard and fires repeatedly while you’re holding down the key; repeating
2. `keypress` - press a character keyboard like `a`,`b`, or `c`, not the left arrow key, home, or end keyboard; repeating
3. `keyup` - release a key on the keyboard

Both `keydown` and `keypress` events are fired before any change is made to the text box, whereas the keyup event fires after the changes have been made to the text box. If you hold down a character key, the `keydown` and `keypress` are fired repeatedly until you release the key.

When you press a non-character key, the `keydown` event is fired first followed by the `keyup` event. If you hold down the non-character key, the `keydown` is fired repeatedly until you release the key.

#### Select a keyboard event

```html
<input type="text" id="message">
```

```js
let msg = document.getElementById('#message');

msg.addEventListener("keydown", (event) => {
    // handle keydown
});

msg.addEventListener("keypress", (event) => {
    // handle keypress
});

msg.addEventListener("keyup", (event) => {
    // handle keyup
});
```

#### Important Keyboard Properties

1. `key` - returns the character that has been pressed
2. `code` - returns the physical key code

For example, if you press the `z` character key, the `event.key` returns `z` and `event.code` returns `KeyZ`.


## Event Delegation

The event delegation refers to the **technique of using event bubbling to handle events at a higher level in the DOM** than the element on which the event originated.

Suppose this:

```html
<ul id="menu">
    <li><a id="home">home</a></li>
    <li><a id="dashboard">Dashboard</a></li>
    <li><a id="report">report</a></li>
</ul>
```

```js
// wrong method

let home = document.querySelector('#home');
home.addEventListener('click',(event) => {
    console.log('Home menu item was clicked');
});

let dashboard = document.querySelector('#dashboard');
dashboard.addEventListener('click',(event) => {
    console.log('Dashboard menu item was clicked');
});

let report = document.querySelector('#report');
report.addEventListener('click',(event) => {
    console.log('Report menu item was clicked');
});
```

The normal, tedious way of adding event handlers shown above is inefficient because: 
- each function takes up memory, which slows the performance
- takes time to assign all the event handlers which causes a delay in the interactivity of the page

Instead of having multiple event handlers, you can **assign a single event handler** to handle all the `click` events:

```js
// right method

let menu = document.querySelector('#menu');

menu.addEventListener('click', (event) => {
    let target = event.target;
	
    switch(target.id) {
        case 'home':
            console.log('Home menu item was clicked');
            break;
        case 'dashboard':
            console.log('Dashboard menu item was clicked');
            break;
        case 'report':
            console.log('Report menu item was clicked');
            break;
    }
});
```

## The dispatchEvent Method
[More info](https://www.javascripttutorial.net/javascript-dom/javascript-dispatchevent/)

This lets you create events generated from code instead of user actions for testing.

**Create a new event:**
```js
let event = new Event(type, [,options]);
```

**The 2 parameters:**
1. type - is a string that specifies the event type such as `'click'`.
2. options - is an object with two optional properties:
	- `bubbles`: is a boolean value that determines if the event bubbles or not. If it is `true` then the event is bubbled and vice versa.
	- `cancelable`: is also a boolean value that specifies whether the event is cancelable when it is `true`.

**By default, the `options` object is:**
```js
{ bubbles: false, cancelable: false}
```

```js
// example
let event = new Event('click');
```


**Example scenario**

```html
<button class="btn">Test</button>
```

```js
let btn = document.querySelector('.btn');

 btn.addEventListener('click', function () {
        alert('Mouse Clicked');
 });

let clickEvent = new Event('click');
btn.dispatchEvent(clickEvent);
```


The `Event` is the base type of `UIEvent` which is the base type of other specific event types such as `MouseEvent`, `TouchEvent`, `FocusEvent`, and `KeyboardEvent`.

It’s a good practice to use the specialized event constructor like MouseEvent instead of using the generic `Event` type because these constructors provide more information specific to the events.


**The isTrusted Method**

If the event comes from the user actions, the `event.isTrusted` property is set to `true`. 

In case the event is generated by code, the `event.isTrusted` is `false`. Therefore, you can examine the value of `event.isTrusted` property to check the “authenticity” of the event.

## Custom Events

Unlike standard events, custom events are events that you define and dispatch yourself. 

Custom events **allow you to create your own communication system** between different parts of your app.

**Why use custom events?** Custom events allow you to decouple code execution, allowing one piece of code to run after another completes.

For example, you can place event listeners in a separate script file and have multiple listeners for the same custom event.


**Create a custom event**
```js
let event = new CustomEvent(eventType, options);
```

**The `CustomEvent()` has two parameters:**
- The `eventType` is a string that represents the name of the event.
- The `options` is an object has the `detail` property that contains any custom information about the event.

**Example**

```html
<div class="note">JS Custom Event</div>
```

```js
function highlight(elem) {
	const bgColor = 'yellow';
	elem.style.backgroundColor = bgColor;

	// create the event
	let event = new CustomEvent('mark', {
		detail: {
			backgroundColor: bgColor
		}
	});
	// dispatch the event
	elem.dispatchEvent(event);
}

// Select the div element
let div = document.querySelector('.note');

// Add border style
function addBorder(elem) {
	elem.style.border = "solid 1px red";
}

// Listen to the highlight event
div.addEventListener('mark', function (e) {
	addBorder(this);

	// examine the background
	console.log(e.detail);
});

// highlight div element
highlight(div);
```


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