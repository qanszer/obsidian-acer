
2025-10-21  13:28

Tags: [[JavaScript]] [[Coding]]

---

# 01 - Numbers


## Operators

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

| Operator   - | Name                                 x |
| ------------ | -------------------------------------- |
| ===          | Strict equality                        |
| !==          | Strict non-equality                    |
| <            | Less than                              |
| >            | Greater than                           |
| <=           | Less than or equal to                  |
| >=           | Greater than or equal to               |

Use `===` and `!==` on Javascript, not the `==` and `!=` because it also tests out whether the datatypes of the values are the same.














---
# 02 - Variables


## Types

There are only 2 types of variables:

1. `let`
2. `const`
3. `var` (older version of `let`)

## Data Types

| Type         - | Description                                                                   x |
| -------------- | ------------------------------------------------------------------------------- |
| number         | integer(whole num) or floating point(decimal num)                               |
| bigint         | 643116n  // n characterizes the number as bigint                                |
| string         | "" , ''  are the same; `` is used for embedding variables                       |
| boolean        | true/false                                                                      |
| null           | represents "nothing", "empty", or "value unknown"                               |
| undefined      | "value is not assigned"                                                         |
| object         | stores collections of data and more complex entities                            |
| symbol         | used to create unique identifiers for objects                                   |

To check a variable's data type:

```js
typeof variableName;
```





---
# 03 - Strings


Syntax to embed a variable inside a string:

```js
let x = 10;
let y = `Use backticks like this to insert a variable: ${x}`;
```








---
# References