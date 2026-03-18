
2026-03-06  12:25 pm

Tags: [[The Odin Project]], [[Coding]]

---
# Problem Solving

This is the most important skill a developer needs.

Problem solving is the core thing software developers do. The programming languages and tools they use are secondary to this fundamental skill.

> 
> *"Problem solving is writing an original program that performs a particular set of tasks and meets all stated constraints."*
> 


---

# Steps in the Problem Solving Process


## 01 - Understand

The first step to solving a problem is understanding exactly what the problem is. If you don’t understand the problem, you won’t know when you’ve successfully solved it and may waste a lot of time on a wrong solution.

To gain clarity and understanding of the problem, **write it down on paper**, **reword it in plain English** until it makes sense to you, and **draw diagrams** if that helps.

> 
> *“If you can’t explain something in simple terms, you don’t understand it.”*
> *— Richard Feynman*
> 

## 02 - Plan

Now that you know what you’re aiming to solve, don’t jump into coding just yet. It’s time to plan out how you’re going to solve it first. Some of the questions you should answer at this stage of the process:

Checklist:

- Does your program have a **user interface**? What will it look like? What functionality will the interface have? Sketch this out on paper.
- What **inputs** will your program have? Will the user enter data or will you get input from somewhere else?
- What’s the **desired output**?
- Given your inputs, what are the **steps necessary to return the desired output**?

The last question is where you will **write out an algorithm to solve the problem**. You can think of an **algorithm** as **a recipe for solving a particular problem**. 

It **defines the steps that need to be taken by the computer to solve a problem** in pseudocode.

## 03 - Divide

From your planning, you should have identified some subproblems of the big problem you’re solving. Pick the smallest or simplest one and start there.

It’s important to remember that **you might not know all the steps that you might need up front, so your algorithm may be incomplete—this is fine**. Getting started with and solving one of the subproblems you have identified in the planning stage often reveals the next subproblem you can work on. Or, if you already know the next subproblem, it’s often simpler with the first subproblem solved.

**Many beginners try to solve the big problem in one go**. **Don’t do this**. If the problem is sufficiently complex, you’ll get yourself tied in knots and make life a lot harder for yourself. Decomposing problems into smaller and easier to solve subproblems is a much better approach.

**Decomposition is the main way to deal with complexity**, making problems easier and more approachable to solve and understand.


In short, **break the big problem down and solve each of the smaller problems until you’ve solved the big problem**.

## 04 - Pseudocode

Pseudocode is writing out the logic for your program in natural language instead of code. It helps you slow down and think through the steps your program will have to go through to solve the problem.

Here’s an example of what the pseudocode for a program that prints all numbers up to an inputted number might look like:

```text
When the user inputs a number
Initialize a counter variable and set its value to zero
While counter is smaller than user inputted number increment the counter by one
Print the value of the counter variable
```


### About Pseudocode

It is a technique used to **describe the distinct steps of an algorithm** in a way that’s easy for anyone with basic programming knowledge to understand.

In the initial state of solving a problem, it helps to **eliminate the limitations offered by a specific programming language’s syntax rules** when we design or validate an algorithm. By doing this, we can **focus our attention on the thought process behind the algorithm and how it will (or won’t) work** instead of focusing on our syntax.


Although pseudocode is a syntax-free description of an algorithm, **it must provide a full description of the algorithm’s logic so that moving from pseudocode to implementation** is merely a task of translating each line into code using the syntax of any given programming language.

### Pseudocode's Rules

1. Always capitalize the initial word (often one of the main six constructs).
2. Make only one statement per line.
3. Indent to show hierarchy, improve readability and show nested constructs.
4. Always end multi-line sections using any of the END keywords (ENDIF, ENDWHILE, etc.).
5. Keep your statements programming language independent.
6. Use the naming domain of the problem, not that of the implementation. For instance: “Append the last name to the first name” instead of “name = first+last.”
7. Keep it simple, concise and readable.

### Importance of Pseudocode

As they put it, “Why write code twice?” That might be correct in the case of simple, straightforward problems. However, as the complexity and the size of the project increases, programmers come to realize how generating pseudocode makes writing the actual code much easier. Pseudocode helps you realize possible problems or design flaws in the algorithm earlier in the development stage, which saves you more time and effort on fixing bugs and avoiding errors down the road.

- It is easier to read when working alongside people like mathematicians, managers, and business partners
- It simplifies code construction, making it easier and faster
- A helpful starting point for [documentation](https://builtin.com/data-science/pseudocode#:~:text=Starting%20Point%20for-,Documentation,-Documentation%20is%20an)
- Easier to edit and discover bugs

---

## Stuck?

First off, **take a deep breath**. Second, **that’s fair**. Don’t worry though, this happens to everyone!

The difference is **the best programmers/problem-solvers are more curious about bugs/errors than irritated**.

#### Things to try when stuck:

- **Debug**: Go step by step through your solution trying to find where you went wrong. “The art of debugging is figuring out what you really told your program to do rather than what you thought you told it to do.”
	
- **Research**: No matter what problem you have, someone has probably solved it. Find that person/ solution. In fact, do this even if you solved the problem! (You can learn a lot from other people’s solutions)
	
- **Reasses**: Take a step back. Look at the problem from another perspective. Is there anything that can be abstracted to a more general approach?
	
- **Starting Anew**: Delete everything and begin again with fresh eyes. I’m serious. You’ll be dumbfounded at how effective this is.


---

## How to Improve? Through Practice

Don’t expect to be great after just one week. If you want to be a good problem-solver, solve a lot of problems!

Practice. Practice. Practice. It’ll only be a matter of time before you recognize that “this problem could easily be solved with .”

So, what you should do is find an outlet to practice. Something that allows you to solve many micro-problems (ideally, something you enjoy).

For me personally, I want to start enjoying solving problems in [Project Euler](https://projecteuler.net/about)

All problems share similar patterns.


> 
> *“Just when you think you’ve successfully navigated one obstacle, another emerges. But that’s what keeps life interesting.*
> 
> *Life is a process of breaking through these impediments — a series of fortified lines that we must break through.*
> 
> *Each time, you’ll learn something.*
> 
> *Each time, you’ll develop strength, wisdom, and perspective.*
> 
> *Each time, a little more of the competition falls away. Until all that is left is you: the best version of you.” — Ryan Holiday ([The Obstacle is the Way](https://www.amazon.com/dp/1591846358/?tag=richardreeze-20))*
> 


---

## References

https://www.theodinproject.com/lessons/foundations-problem-solving