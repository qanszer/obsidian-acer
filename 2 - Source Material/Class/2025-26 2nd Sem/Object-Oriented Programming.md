 
2026-01-30  19:55

Tags: [[School]] [[Coding]] [[Java]]

---
# Object-Oriented Programming  |  2025-26

---

# 1st Semester

## Prelim

### 02/02/26 - Creating Classes in Java and UML Diagrams

#### Java Name Case Standard

1. Class - PascalCase
2. Attribute - camelCase
3. Method - camelCase
4. Constant - ALL CAPS
5. Package - all lower

	Always think deliberately on what data type to use. Because changing it after it has been established in a used system can cost millions.

#### UML Class Diagram
The code namecase standard is still applied here

1. "-" is private
2. "+" is public
3. "#" is protected

Void - no return value
  
#### Parameter Directions

1. in - input only, does not return an output
2. out
3. inout

example: method(in p1:type): type

#### URL Diagram Example

| ClassName                                                                                  |
| ------------------------------------------------------------------------------------------ |
| - attributeOne: dataType                                                                   |
| + attributeTwo: dataType                                                                   |
| + methodOne(in/inout/out attributeOne: dataType): void                                     |
| + methodTwo(in attributeOne: dataType, in attributeOne: dataType): dataTypeOrInOutOfMethod |


---

### 02/05/26 - Java Syntax

#### Importance of Comments

- only you and God know your code when you made it
- when you revisit your code after ~6 months, you'll have a hard time understanding any of it if you don't put comments

#### Data Type Good Practice

In Java, instead of using the normal data types like `int`, `double`, `float`, etc
Use `var` instead

#### Printing Syntax:

`System.out.println("variable");`

#### For Simple Conditionals:

```java
int time = 20;
String result = (time < 18) ? "Good day." : "Good evening.";
System.out.println(result);
```

#### Simple Example for a Nested Loop:

```java

// The Code

for (int1 = 0; i < 5; i++) {

	System.out.printIn(int1);

	for (int2 = 0; y < 10; y++) {
	
		System.out.printIn(int2);
		
	}
}

// The Output

0+0
0+1
0+2
0+3
...
0+9

1+0
1+1
1+2
...
1+9

...

5+0
...
5+9

```


---

## Midterm


### 03/09/26 

#### Note About Else If

If your code block has a long list of else if like:

```
else () {
} else if () {
} else if () {
} else if () {
} else if () {
} else if () {
} else if () {
} else if () {
} else if () {
}
```

It is better to make it like this:

```
if () {
}
if () {
}
if () {
}
if () {
}
```

This way, the execution does not have to go through each if statement.


For `for` loops, `continue` and `break` are frequently used in real programs.


#### Stored Procedure

- Inside of Stored procedure: TSQl - Transaction SQL
- What's inside depends on the programmer
- Benefit: you can use it without editing the website itself
- Best for maintaining websites and systems
- You can combine `INSERT` and `SELECT` (the most common combi) in one statement and many other combinations


**INSERT-SELECT**

```sql
INSERT INTO OldStudent(Id, Name, Course) // ALWAYS include the column names for safety and to save yourself the trouble of debugging for 3-6 hours because of missing this)
SELECT Id, Name FROM Student
```


#### Syntax for Stored Procedure

```
CREATE PROCEDURE ProcedureName
(
@columnName dataType,
@columnName dataType
)
```


---

### 03/10/26 - Arrays

**Syntax**
```java
int[] numbers = {10, 20, 30, 40, 50};
```


**2 Methods of Printing Arrays**

1. Standard for loop
```java
for (int i = 0; i < numbers.length; i++) {
	System.out.print(numbers[i] + " ");
}
```

2. Foreach loop specially for arrays
```java
for (int element : numbers) {
	System.out.print(element + " ");
}
```


---

### 03/12/26 - Multidimensional Arrays

Basically arrays within arrays

**Syntax**
```java
int[][] matrix = {
	{1,5,7},
	{8,2,6,3},
	{9,2},
	{1},
	{2,3}
};
```

On the code above, the first array (main array) is the outermost bracket. See below

```java
int[][] matrix = { // this one
	{1,5,7},
	{8,2,6,3},
	{9,2},
	{1},
	{2,3}
}; // and this one
```

That means that the ones inside it are only counted as 1 single element for each that are separated by a comma. See below

```java
int[][] matrix = {
	{1,5,7}, // separated by comma here, meaning it's only 1 element
	{8,2,6,3}, // 2nd element separated by comma
	{9,2}, // 3rd element
	{1}, // 4th
	{2,3} // 5th element
};
```

They can be called inside the code through `indexes`. See below

```java
int[][] matrix = {
	{1,5,7}, // this whole line can be called with matrix[0]
	{8,2,6,3}, // matrix[1]
	{9,2}, // matrix [2] 
	{1},
	{2,3}
};
```

The thing is, each of those elements are arrays by themselves. See below

```java
int[][] matrix = {
	{1,5,7}, // 1st element can be called with matrix[0][0]
	{8,2,6,3},
	{9,2},
	{1},
	{2,3}
};
```

The output of calling `matrix[0][0]` is 1

But if you were to call `matrix[0]`, you will get a hashcode of the element. The only way to solve this is through a for loop. Or if you don't mind having the square brackets, then you can do another method

For loop wherein the output has no square bracket:
```java
for (int i = 0; i < matrix[0].length; i++) {
	System.out.print(matrix[i] + " ");
}
```


**Example Exercise**

1. Expected Output
```
1 5 7
8 2 6 3
9 2
1
2 3
```

2. Solution
```java
// multidimensional array variable
int[][] matrix = { 
	{1,5,7},
	{8,2,6,3},
	{9,2},
	{1},
	{2,3}
};

for (int i=0;  i < matrix.length; i++) { // 1st loop is for the vertical length of the output + the actual elements
	for (int j=0; j < matrix[i].length; j++) { 
		System.out.print(matrix[i][j] + " ");
	}
	System.out.println(); // To add new lines
}
```


---

## Finals


### Date - Topic

#### Subtopic



---

# 2nd Semester
## Prelim


### Date - Topic

#### Subtopic



---

## Midterm


### Date - Topic

#### Subtopic



---

## Finals


### Date - Topic

#### Subtopic






