
2026-03-10  03:40 pm

Tags: [[The Odin Project]], [[Coding]]

---
# Understanding Errors

Error messages provide developers with a treasure trove of knowledge, and tell you everything you need to know about how to resolve them.

**Being able to parse error messages and warnings** without fear will enable you to effectively debug your applications, receive meaningful help from others, and empower yourself to push forward when faced with an error.


**Anatomy** - it is a type of object built into JS that consists of a name/type and a message.


## Types of Errors

1. `ReferenceError`
	- Is thrown when one refers to a variable that is not declared and/or initialized within the current scope
	- Either the **variable does not exist** (within the current scope) or it has been **spelled incorrectly**
2. `SyntaxError`
	- Occurs when the code is not written correctly in accordance with the grammatical rules of the programming language
3. `TypeError`
	- when an **operand or argument** passed to a function is **incompatible with the type expected** by that operator or function
	- or when attempting to **modify a value that cannot be changed**
	- or when attempting to **use a value in an inappropriate way**


**Stack Trace** - helps you understand **when** the error was thrown in your application, and **what** functions were called that led up to the error. [Example here](https://www.theodinproject.com/lessons/foundations-understanding-errors#introduction:~:text=error%20is%20the-,stack%20trace,-.%20This%20helps%20you)


## Tips for Resolving Errors

1. Understand that the **error message is your friend**, not your enemy. It tells you exactly what is wrong with your code and which lines to examine to find the source of the error
2. **Google the error** because chances are that you can find a fix or explanation in the internet
3. **Use the debugger**. It is an extremely valuable tool and every programmer should know how to use it
4. **Console.log() is a popular choice for quick debugging**. But for more involved troubleshooting, use the debugger tool. Other useful methods include `console.table()`, `console.trace()`, and more


## Errors vs. Warnings

Errors
- **Stops the execution of your program** or whatever process you may be attempting to run and **prevent further action**. 
- Usually color red

Warnings 
- **Messages** that provide you insight **on potential problems that may not necessarily crash your program** at runtime, or at all. 
- Usually color yellow



---

# References

https://www.theodinproject.com/lessons/foundations-understanding-errors