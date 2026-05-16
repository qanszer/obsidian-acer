 
2026-01-30  19:55

Tags: [[School]], [[Coding]], [[Java]]
Professor: Sir Jayson Ocampo

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


### 03/09/26 - If Statement Optimization + SQL

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
INSERT INTO OldStudent(Id, Name, Course) -- ALWAYS include the column names for safety and to save yourself the trouble of debugging for 3-6 hours because of missing this)
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

### 03/19/26 - Useful Array Functions
[More info for these functions](https://docs.oracle.com/javase/8/docs/api/java/util/Arrays.html)

`Arrays.binarySearch()`

`Arrays.sort()`

`Arrays.equals()`

`Arrays.fill()`

`Arrays.toString()`

`Arrays.copyOf()`


---

### 03/23/26 - Types of Arrays + SQL Joins

**Fixed Arrays**
1. `int[]` - 1 dimensional array
2. `int[][]` - 2d array
3. `int[][][]` - 3d array

They are rarely used in real programming environments.

The types of arrays that are always used are `LinkedList` and `ArrayList`.

**ArrayList**
- are resizeable arrays
- elements can be added and removed easily

```java
ArrayList<String> cars = new ArrayList<String>();
cars.add("BYD");
```

ArrayLists usually don't have normal data types as its data type (String, int, etc). It's always usually objects like this:

```java
ArrayList<Student> students = new ArrayList<Student>();
```


*Copy-paste from the internet:*

**When to Use Which?**

Use [ArrayList](https://docs.oracle.com/en/java/javase/25/docs/api/java.base/java/util/LinkedList.html) When:
- **Reading data frequently:** You need fast lookup by index (e.g., a list of search results).
- **Most operations are at the end:** Appending elements to the end is very efficient 
- **Memory is a concern:** You want to minimize overhead per element [8, 12].
- **Note:** In modern Java, `ArrayList` is the **recommended default** because modern CPUs are highly optimized for sequential memory access [9, 13, 14]. 

Use LinkedList When:
- **Frequent insertions/deletions at the start:** It doesn't need to shift the whole list like an array [10, 13].
- **Implementing Stacks or Queues:** It natively implements `Deque` and `Queue` interfaces, providing efficient `addFirst()`, `removeFirst()`, and `peek()` operations [6, 29].
- **Memory is flexible:** You don't mind the overhead of storing two extra pointers (references) for every single element [3, 6].



**SQL JOINS**

Left join is the one that's used 90% of the time in real coding environments

**Left Join**
- gets all the columns and rows from the 1st table, but only gets the matching columns and rows of the 2nd table to the 1st



---

### 03/24/26 - Continuation to LinkedLists

**LinkedList Syntax**

```java
LinkedList<int> matrix;
```

```java
LinkedList<String> Students = new LinkedList<>();
```


**LinkedList vs ArrayList**

Use `LinkedList` if your purpose is mainly modifications of data. 
Use `ArrayList` if mainly for accessing of data.


`.size()` is the `.length()` equivalent of arrays for ArrayLists and LinkedLists
```java
Students.size();
```


**LinkedList Methods**

.pop() - removes from the top of the array
```java
Students.pop();
```

.remove() - selected removal anywhere in the array
```java
Students.remove("Michael");
Students.remove(0);
```

.clean() - removes all elements
```java
Students.clean();
```

.addFirst()
```java
Students.addFirst("Jason"); // adds Jason to the bottom of the stack
```

.addLast()
```java
Students.addLast("Jen"); // adds Jenny to the top of the stack
```

.clone() - copies the elements inside a `LinkedList`, but as an `object` data type
```java
new Studentss = Students.clone(); // this does not, see below for solution
```


**Useful Ways of Casting(Converting)**

This will be a normal part of your routine in real coding environments.

```java
int x = int(2.0); // to catch calculations in your preferred way
```

```java
new Studentss = (LinkedList<String>)Students.clone();
```

but another method that's easier to clone a LinkedList is:
```java
LinkedList<String> newStudents = new LinkedList<>(Students);
```


**Good Practice in the Deletion/Modification of Elements**

```java
If (!Students.isEmpty()) {
	Students.removeLast();
}
```

This avoids a silent error wherein the code removes something that does not exist in the first place, resulting in a future bug that is hard to find.


---

### 03/26/26 - Continuation to LinkedLists

Cleaner LinkedList initialization:
```java
var matrix = new LinkedList<Integer>();
```

Copy a LinkedList:
```java
var matrixClone = new LinkedList<Integer>(matrix);
```

Two-Dimensional LinkedList Array:
```java
var matrix = new LinkedList<LinkedList<Integer>>();

var firstRow = new LinkedList<Integer>();
firstRow.add(1);
firstRow.add(1);
firstRow.add(1);
matrix.add(firstRow);

var secondRow = new LinkedList<Integer>();
secondRow.add(2);
secondRow.add(2);
secondRow.add(2);
matrix.add(secondRow);
```

Accessing the 2d LinkedList Array:
```java
System.out.println(matrix.get(0).get(2));
```

Displaying 2d LinkedList:
```java
for(LinkedList<Integer> row : matrix) {
	for(Integer value : row) {
		System.out.print(value + " ");
	}
	System.out.print();
}
```



---
### 04/07/26 - Put JSON inside LinkedLists

```java
// Items JSON

var itemList = new LinkedList<Items>();
    
public class Items {
	int id;
	String name;
	double price;
	LinkedList<Items> subItems;
}
```

```java
// Sections JSON

var sectionsList = new LinkedList<Sections>();

public class Sections {
	String sectionId;
	String sectionName;
	LinkedList<Students> students;
}

public class Students {
	int id;
	String name;
	int age;
	double grade;
}
```

```java
// Platforms JSON

var platformList = new LinkedList<Platforms>();

public class Platforms {
	LinkedList<Stores> stores;
}

public class Stores {
	String storeName;
	LinkedList<Orders> orders;
}

public class Orders {
	String orderId;
	LinkedList<Products> products;
}

public class Products {
	String name;
	double price;
	int quantity;
}
```


**Tip**: Always copy the existing naming cases on the websites you copied the JSON from.


**Flow when developing projects**
1. Database first
2. Object with class
3. Logic


---
### 04/20/26 - APIs and Postman

*Advice*: In production databases, **never delete records**. If it needs to be removed, only hide them through a column like `isDeleted` with 1 and 0 as the values.


---
### 04/21/26 - Connecting Java to an API

1. Download the Gson jar file online
2. Add to netbeans through Properties > add Jar folder > choose jar file
3. Import to the project
```java
import com.google.gson.Gson;
import com.google.gson.reflect.TypeToken;

import java.io.InputStreamReader;
import java.lang.reflect.Type;
import java.net.HttpURLConnection;
import java.net.URL;
import java.util.List;
```
4. Declare the url and setup the student class
```java
// GET
try {
	URL url = new URL ("http://api");
	HttpURLConnection conn = (HttpURLConnection) url.openConnection();
	conn.setRequestMethod("GET"); // request data from the internet
	
	InputStreamReader reader = new InputStreamReader (conn.getInputStream());
	
	Gson gson = new Gson();
	Type studentListType = new TypeToken<List<Student>>(){}.getType();
	
	List<Student> students = gson.fromJson(reader, studentListType); // store students here
	
	for(Student stud : students) {
		System.out.println("Student Name: " + stud.getFullName() + "\nContact No: " + stud.getContactNo());
	}
}
catch (Exception e) {
	e.printStackTrace();
}

public class Student {  
    private String id,fullName,contactNo;  
  
    public String getFullName(){ return fullName; }  
    public String getContactNo(){ return contactNo; }  
    
    public void setFullName(String fullName){ this.fullName = fullName; }  
    public void setContactNo(String contactNo){ this.contactNo = contactNo; }  
}
```


#### Benefits of using an API

![[Pasted image 20260421134228.png]]

No need to frequently deploy through the use of API. You just have to alter the stored procedure.


---

## Finals


### 04/28/26 - Public, Private, Protected, and Default

It is good practice to declare all variables inside classes as private to prevent direct access (protection against hackers), and then make get-setter methods to get and update them as needed.

```java
public class BankAccount {
	private double balance;
	
	public double getBalance() { return balance; }
	public double setBalance(double balance) { this.balance = balance};
}
```

It is much easier to do this in C#

```C#
String fullName { get; set; }
```


#### Best Practices

1. Keep fields/attributes private - declare class variables as private and expose them through controlled methods
2. Provide meaningful methods - should represent clear actions or behaviors of the class
3. Provide meaningful methods - objects using constructors for cleaner and more reliable code
4. Follow naming conventions - different for every programming language, but for java:
	- class: PascalCase
	- variables and methods: camelCase
5. Validate input date - always validate inputs in setters or methods to prevent invalid states
6. Keep classes focused (single responsibility principle) - a class should only have 1 responsibility or purpose


**Advice**: Use claude for reports - attach 2 excel sheets and compare them and tell the difference between the two

The real challenge in programming is not in writing code, but in improving its performance from 30 seconds to 3-5 seconds.


**Advice for SQL**: Always use alias `AS` because it's very helpful for joins


---
### 04/28/26 - Inheritance, Method Overriding, & Super

**Inheritance** allows the child class to inherit the attributes and methods of the parent class.

Inheritance syntax:

```java
class Dog extends Animal {
	
}
```


**Method overriding** allows the child class to replace a method of a parent class, but only within its class.

These conditions need to be met for it to be allowed:
- same method name
- same parameters
- same return type (or covariant)

Method override syntax:

```java
- class Animal {
-     void sound() {
-         System.out.println("Animal makes a sound");
-     }
- }

- class Dog extends Animal {
-     @Override
-     void sound() {
-         System.out.println("Dog barks");
-     }
- }
```


The **Super** keyword allows the child class to access its parent class's methods, variables, and constructor

```java
// method
super.sound();

// variable
super.name

// constructor
super();
```

```js
for (User user : DataStore.users) {
	if (username.equals(user.username) 
			&& password.equals(user.password) 
			&& role == user.role
			&& user.isActive) {
		return user;
	}
}
```


---

### 05/12/26 - Exception Handling


#### Types of Errors

1. Syntax error - is caught at compile time; easiest to find
2. Logic error - does not cause any errors at all, but produces the wrong expected output; hardest to find
3. Runtime error - is caught during execution when an input or event is not what is expected; solved using try-catch blocks


#### Try, catch, finally

```java
try {
	// the risky code here
}
catch (NumberFormatException e) {
	// if input is not a number
}
catch (Exception e) {
	// handles the other error types; you can put as many catch blocks as you want
}
finally {
	// always executes
}
```

If your execution did not reach `finally`, then an error occured above and was not caught


**Advice**: The exceptions used in real coding environments are always the general/generic version. Specific exceptions are only used when the tester wants it to be specific. It is easier on your part in this way also.

#### Common Built-in Exceptions

The following table lists common exceptions you will encounter most frequently in Java development:

| Category                | Exception Name                   | Description                                                                              |
| ----------------------- | -------------------------------- | ---------------------------------------------------------------------------------------- |
| **Unchecked (Runtime)** | `NullPointerException`           | Occurs when trying to access an object reference that is `null`.                         |
|                         | `ArrayIndexOutOfBoundsException` | Thrown when an array is accessed with an illegal index.                                  |
|                         | `ArithmeticException`            | Thrown for exceptional arithmetic conditions, like division by zero.                     |
|                         | `IllegalArgumentException`       | Thrown when a method receives an inappropriate argument.                                 |
|                         | `NumberFormatException`          | Occurs when trying to convert a string to a number format incorrectly.                   |
|                         | `ClassCastException`             | Thrown when attempting to cast an object to an incompatible subclass.                    |
| **Checked**             | `IOException`                    | Base class for exceptions that occur during I/O operations (e.g., file/network failure). |
|                         | `FileNotFoundException`          | Specific `IOException` when a file cannot be found on the disk.                          |
|                         | `SQLException`                   | Thrown when interacting with a database encounters an error.                             |
|                         | `ClassNotFoundException`         | Raised when the JVM fails to find a class file by its string name.                       |

