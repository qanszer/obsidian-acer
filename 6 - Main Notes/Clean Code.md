
2026-03-19  07:29 am

Tags: [[Coding]], [[The Odin Project]]

---
# Clean Code

This is a copy-paste + own notes from The Odin Project.


## Main Learnings

1. Code can tell you _how_ the program works; comments can tell you _why_ it works
2. Instead of imagining that our main task is to instruct a computer what to do, let us concentrate rather on explaining to human beings what we want a computer to do
3. Sometimes when writing code, you'll think “I should comment this”. The first and proper response to that feeling is to refactor the code. You should always write your code as if comments didn’t exist. After you’ve refactored, if you still feel a comment is necessary, then by all means add one.

## Introduction

You might think that the majority of a developer’s work involves writing code. However, in reality, a significant amount of time is spent on _reading_ code. This includes code written by:
- other team members
- people who are no longer part of your team
- and even code that you wrote two weeks ago but may not remember much about

Don’t think of these principles as something you need to master immediately.

Everybody writes messy code sometimes, even professionals. What we want to do here is give you some guidelines that can help improve the readability of your code as you go along. The more you write code, the better it will become, both in terms of readability and other aspects.

Test out these ideas and try to incorporate them into your thought process while writing code, but don’t beat yourself up for not writing elegant, crystal-clear code. 

Focus on gradual improvement, not perfection.

## Use Conventions

Conventions improve code readability and maintainability. Until a time comes where you need to follow a specific set of conventions, it is sensible to follow some convention and be consistent with them.

The camelCase naming convention is the most common in JavaScript so use that as the default, but in every organization, they will have their own set of conventions and you should follow it.

## Naming Functions and Variables

#### 01 - It is descriptive
The function should do what its name suggests. Nice, clean, and understandable.

#### 02 - Use consistent vocabulary
Like this:
```javascript
// Consistent naming
function getPlayerScore();
function getPlayerName();
function getPlayerTag();
```
Not this:
```javascript
// Inconsistent naming
function getUserScore();
function fetchPlayerName();
function retrievePlayer1Tag();
```

Variables should begin with a noun.
Functions should begin with a verb.

#### 03 - Use immediately understandable names

Don't use "magic values" like `setTimeout(stopTimer, 3600000);`
What does the 3600000 mean there? You can't tell immediately right?

Improve it by using a descriptive variable:
```javascript
const ONE_HOUR = 3600000; // Can even write as 60 * 60 * 1000;
setTimeout(stopTimer, ONE_HOUR);
```

## Indentation and Line Length

Many style guides vary and recommend different options, and one is not really superior to the other.

What actually matters is *consistency*.

Generally, your code will be easier to read if you manually break lines that are longer than about 80 characters. Many code editors have a line in the display to show when you have crossed this threshold. 

When manually breaking lines, you should try to break immediately _after_ an operator or comma.

```javascript
// This line is a bit too long
let reallyReallyLongLine = something + somethingElse + anotherThing + howManyTacos + oneMoreReallyLongThing;

// You could format it like this
let reallyReallyLongLine =
  something +
  somethingElse +
  anotherThing +
  howManyTacos +
  oneMoreReallyLongThing;

// Or maybe like this
let anotherReallyReallyLongLine = something + somethingElse + anotherThing +
                                  howManyTacos + oneMoreReallyLongThing;
```

Different formats aren’t necessarily right or wrong, and different people may prefer different things. Do things in a way that makes sense to you, and stay consistent with it.

## About Comments

Comments are a great tool but like any good tool, they can be misused. Especially for someone early in their coding journey, it might be tempting to have comments that explain _everything_ the code is doing.

The same applies to code that is no longer used. If you need it again in the future, just turn to your git commits. Commenting out something while testing something else is, of course, ok, but once a piece of code is not needed, just delete it. Don’t have something like this hanging around in your files:

By using git, all this information will be neatly organized in the repository and readily accessible with `git log`.

#### Comments tell why, not how

Good comments explain the _reasons_ behind a piece of code. Sometimes you won’t even need a comment at all!

Say we had a string where part of the text was inside square brackets and we wanted to extract the text within those brackets.

```javascript
// Function to extract text
function extractText(s) {
  // Return the string starting after the "[" and ending at "]"
  return s.substring(s.indexOf("[") + 1, s.indexOf("]"));
}
```

The comments just describe what we can tell from the code itself. Slightly more useful comments could explain the reasons behind the code.

```javascript
// Extracts text inside square brackets (excluding the brackets)
function extractText(s) {
  return s.substring(s.indexOf("[") + 1, s.indexOf("]"));
}
```

But often, we can make the code speak for itself without comments.

```javascript
function extractTextWithinBrackets(text) {
  const bracketTextStart = text.indexOf("[") + 1;
  const bracketTextEnd = text.indexOf("]");
  return text.substring(bracketTextStart, bracketTextEnd);
}
```

**This doesn’t mean good code should lack comments.** Let’s look at an example where a comment serves a helpful purpose:

```javascript
function calculateBMI(height, weight) {
  // The formula for BMI is weight in kilograms divided by height in meters squared
  const heightInMeters = height / 100;
  const bmi = weight / (heightInMeters * heightInMeters);
  return bmi;
}
```


> 
> You should first strive to make your code as simple as possible to understand without relying on comments as a crutch. Only at the point where the code _cannot_ be made easier to understand should you begin to add comments.
> 

#### Avoid abusing comments

Examples to avoid:
- Writing explanatory notes to self _(e.g. /* Will finish this later… */)_.
- Blaming stuff on other people _(e.g. /* John coded this. Ask him. */)_.
- Writing vague statements _(e.g. /* This is another math function. */)_.
- Erasing chunks of code. Sometimes people are not sure of erasing things and it’s not absolutely evil to comment that code instead. What’s not right is to just leave it afterwards. It’ll be terribly confusing. If the code will be documented via embedded comments, the team members need to make sure those comments are there for a reason.

Examples of good comments:
- Authoring specifications _(e.g. /* Coded by John, November 13th 2010 */)_.
- Detailed statements on the functionality of a method or procedure _(e.g. /* This function validates the login form with the aid of the e-mail check function */)_.
- Quick notifications or labels that state where a recent change was made _(e.g. /* Added e-mail validation procedure */)_.

![[Pasted image 20260319090128.png]]

## Avoid Large Functions

One can come across functions that consist of up to a hundred lines of code, and this tends to become confusing.

A better practice would be to **break up large functions** into smaller ones.

## Avoid Mixing of Coding Languages

In-line CSS styling and scattered JavaScript tags with short procedures within them are very good examples of incorrect mixing of coding languages throughout your development process.

Having the appropriate divisions between different coding languages will give order to the logic applied.

## Summarize your Imports

If there are too many style sheets, they can probably be summarized into one or two.

This won’t only save space and make things look cleaner, but it will also save loading time. Each imported file is an HTTP request that tampers with the performance of your application. So apart from being a consideration for tidiness, it is also a consideration for efficiency.

## Conclusion

Now that we’ve covered these ideas, it’s good to return to the reminder we shared at the start. Don’t try to write perfectly clean code, this will only lead to frustration. Writing “spaghetti” is inevitable; everyone does it sometimes. Just keep these ideas in mind, and with time and patience, your code will start to get cleaner.

Learning to write clean code is a process of constant improvement.

> 
> *"Great code comes from experience. Experience comes from not-so-great code."*
> 


---

# References

https://www.theodinproject.com/lessons/foundations-clean-code#use-searchable-and-immediately-understandable-names