 
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

### 02/10/26 - Topic

#### Subtopic









---

## Midterm


### Date - Topic

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






