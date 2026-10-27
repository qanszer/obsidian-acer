
2026-10-19  07:56am

Tags: [[Coding]], [[Practical Advice]]

---

This is advice from google gemini.

---

### Is angular better than react?

**Neither is universally better** than the other; the right choice depends entirely on your project's needs, team expertise, and long-term goals. **React** is an unopinionated UI library backed by [Meta](https://about.meta.com/) that offers ultimate flexibility, while **Angular** is a robust, "batteries-included" framework backed by Google that enforces a strict architectural structure.

According to data like the [Stack Overflow Developer Survey](https://survey.stackoverflow.co/), **React** dominates overall market share with roughly 44.7% adoption compared to **Angular's** 18.2%. However, both tools have evolved significantly—with Angular introducing fine-grained reactivity via Signals and React expanding into full-stack paradigms with Server Components—making them both highly capable for modern web development.

---

Direct Comparison

|Feature|React|Angular|
|---|---|---|
|**Type**|UI Library (Needs external tools for routing/state)|Full-fledged Framework (All-in-one platform)|
|**Philosophy**|Flexible, "choose-your-own-adventure"|Opinionated, structured, standardized|
|**Language**|JavaScript or TypeScript (Optional)|TypeScript (Enforced by default)|
|**Data Binding**|One-way data flow|Two-way data binding (Optional)|
|**Learning Curve**|Shorter initially, but gets complex at scale|Steeper initial curve, but easier to maintain later|
|**Job Market**|Larger overall market, dominant in startups|Growing heavily in corporate & enterprise sectors|

---

When to Choose React

- **Startups and MVPs:** React allows you to build and iterate quickly without fighting a massive boilerplate configuration.
- **Flexibility Matters:** If you want total freedom to select your own routing, state management (like Zustand or Redux), and build tools.
- **Maximizing Job Postings:** Because it owns the largest market share, there are technically more total job openings available for React developers.
- **Cross-platform Needs:** React makes it incredibly straightforward to pivot to mobile app development using [React Native](https://reactnative.dev/). 

When to Choose Angular

- **Large Enterprise Projects:** Angular provides a standardized way to do everything (routing, HTTP requests, forms). This means any developer can jump into any Angular codebase and instantly understand its layout.
- **Long-Term Systems:** It features predictable release schedules and robust automated CLI migration tools (`ng update`), significantly reducing dependency maintenance headaches over time.
- **Strict Type Safety:** Angular relies natively on [TypeScript](https://www.typescriptlang.org/) and deep object-oriented principles, making it highly favored by teams with Java or .NET backgrounds.
- **Reduced Decision Fatigue:** If you prefer having the "right way" to write code already decided for you by the framework.

---

### Capstone framework advice

**Go with React.** Do not switch to Angular just for this capstone project.

While your professor’s recommendation makes sense from a traditional corporate standpoint, it creates a massive, unnecessary hurdle for your specific situation. Because your capstone starts in **January 2027**, switching to Angular right now is highly risky.

Here is a practical breakdown of why sticking to React is the smartest move for your timeline, your team dynamic, and your learning path.

---

1. Why Your Professor Said That (and why it doesn't matter for you)

Your professor is looking at this from an **enterprise architecture** lens.

- Historically, Microsoft and Google technologies aligned heavily in the corporate world. C# and Angular both enforce strict **object-oriented programming (OOP)** and strong TypeScript paradigms.
- Modern ASP.NET Core is actually entirely decoupled from the frontend. It serves as a **REST API** that returns standard JSON data.
- A REST API does not care if the frontend fetching its data is React, Angular, or raw HTML. React handles HTTP requests (via `fetch` or `Axios`) to an ASP.NET backend exactly the same way Angular does.

2. The Learning Curve vs. Your 2-Month Deadline

You are currently in the intermediate HTML/CSS section of The Odin Project. You still need to learn advanced JavaScript, asynchronous programming, and API integration before you even touch a frontend framework.

- **The React Path:** React is essentially "just JavaScript." Once you master JavaScript objects, arrays, and functions, React will feel like an extension of what you already know. You can fast-track to the React section of The Odin Project if you need to build this capstone by January.
- **The Angular Path:** Angular requires you to learn an entire ecosystem all at once. You will have to learn TypeScript, Modules, Components, Directives, Services, Dependency Injection, and RxJS (reactive programming) before you can build a single functional page. Trying to learn all of that _and_ build a capstone in two months is a recipe for extreme burnout.

3. Maintain Your Momentum with The Odin Project

The Odin Project is one of the best web development curriculums available because it forces deep, cumulative learning. If you pivot to Angular now:

- You break the continuity of your current curriculum.
- You will have to abandon your primary learning resource right when you need it most to scramble for fragmented Angular tutorials.
- Once the capstone ends, you will have to mentally reset to finish The Odin Project's React track.

---

How to Coordinate with Your C# Partner

Since your backend teammate is using ASP.NET, you can easily work together by treating the project as two entirely separate entities that talk to each other over the network:

1. **Build a Decoupled Architecture:** Have your partner build the ASP.NET Core project strictly as a **Web API**. They will create endpoints (e.g., `https://localhost:5000/api/users`) that output JSON data.
2. **Use Swagger/OpenAPI:** ASP.NET has built-in support to auto-generate a Swagger documentation page for APIs. Your partner can just give you the Swagger link, and you will see exactly what data you need to send and receive from your React app.
3. **Enable CORS:** Your partner _must_ enable **CORS (Cross-Origin Resource Sharing)** in their ASP.NET `Program.cs` file to allow your local React server (usually running on port 3000 or 5173) to talk to their C# server.


- Can you ask your partner if they are comfortable building a **pure Web API**, or were they planning to use **Blazor / MVC** templates?

---

### Sections to do and skip on Odin

#### Javascript Course

Yes, **you can strategically skip and streamline specific sections** of The Odin Project to fast-track your path to React in time for your January 2027 capstone.

Because React is a frontend library that relies heavily on modern JavaScript, you **cannot skip core JavaScript fundamentals**. Doing so will make React impossible to understand. However, you can bypass sections that focus on advanced standalone CSS design or backend infrastructure that your partner is already handling in C#.

Below is a breakdown of what you can safely skip, what you must skip (for now), and what is non-negotiable.

Out of the 40+ items in that syllabus, you can condense your focus down to just **12 critical lessons** and **3 downscaled projects**.

To hit your January 2027 deadline, everything else can be completely skipped, heavily skimmed, or deferred until after graduation.

---

🟢 Phase 1: Organizing Your JavaScript Code (Crucial for React Syntax)

React components are fundamentally built on modern JavaScript objects, modules, and functions. Skip the complex OOP layout, but nail down these syntax pieces.

- **Lesson: Organizing Code with Objects** _(Read carefully)_
- **Lesson: Object Constructors** _(Read carefully)_
- **Project: Library** ➔ **[DO THIS PROJECT]** Keep it very simple. Do not over-stylize it. This cements how to store and access data structures.
- **Lesson: Factory Functions and the Module Pattern** _(Read carefully – highly relevant to how React handles state and scope)_
- **Project: Tic Tac Toe** ➔ **[DO THIS PROJECT]** This is a rite of passage for frontend devs. It forces you to manage "application state" cleanly in pure JS before React does it automatically for you.
- **Lesson: ES6 Modules** ➔ **[CRITICAL]** React code is 100% split across files using `import` and `export`. You must master this.
- **Lesson: JSON** ➔ **[CRITICAL]** This is the exact format your teammate's ASP.NET backend will use to send data to your frontend.

🔵 Phase 2: JavaScript in the Real World

Skip the massive project here, but learn how web forms process user input.

- **Lesson: Form Validation with JavaScript** ➔ **[CRITICAL]** Your capstone will undoubtedly require user logins, registrations, or data entries. You need to know how to validate inputs.

🟡 Phase 3: Asynchronous JS & APIs (The Most Critical Section)

This is the absolute bridge between your React frontend and your partner's C# backend. Spend the most time here.

- **Lesson: Asynchronous Code** _(Understand callbacks and promises)_
- **Lesson: Working with APIs** _(Learn how `fetch()` works)_
- **Lesson: Async and Await** ➔ **[CRITICAL]** This is the modern, cleanest way to write API calls. You will use this exact syntax inside React.
- **Project: Weather App** ➔ **[DO THIS PROJECT]** This is your ultimate trial run for the capstone. It forces you to grab external data, parse the JSON, and render it to the page.

---

❌ What to Skip Completely to Save Time

Grouped by section, these can be bypassed to keep your timeline on track:

- **Skip completely from "Organizing Your Code":** _Classes, npm, Webpack, Restaurant Page, Revisiting Webpack, OOP Principles, Todo List._
    - _Why:_ React sets up build tools and package management for you natively (usually via modern tools like Vite). You do not need to waste 2 weeks struggling to configure Webpack manually.
- **Skip completely from "Real World":** _Linting, ECMAScript._
- **Skip completely from "Testing":** _Testing Basics, Testing Practice, More Testing._
    - _Why:_ Writing unit tests is great for enterprise code but takes too long to learn when rushing an MVP capstone.
- **Skip completely from "Computer Science":** _Everything (Recursion, Time/Space Complexity, Linked Lists, HashMap, Trees, Knights Travails)._
    - _Why:_ This is data structures and algorithms material. It is vital for passing technical job interviews later on, but it is 100% irrelevant to building a functioning React user interface next month.
- **Skip completely from "Finishing Up":** _Project: Battleship._
    - _Why:_ This project takes students anywhere from 2 to 4 weeks to complete using manual DOM manipulation. Skip it and allocate those weeks directly to learning React.


---
#### Git and team collaboration

**Do not skip the Git section.** It is absolute non-negotiable prerequisite knowledge for a group project.

Because you are working in a **group of 4**, trying to build this capstone without Git would be a logistical nightmare. You would constantly overwrite each other's code, struggle to merge your frontend with your partner's C# backend, and waste hours manually emailing code files back and forth.

Here is exactly how you should approach this section to save time while getting exactly what your team needs:

🟢 What to Learn from the Git Section

Focus heavily on the concepts of collaboration. You do not need to memorize every complex command, but everyone in your group must understand the workflow.

- **Lesson: Working with Remotes** ➔ **[CRITICAL]** This teaches you how to connect your local computer to **GitHub**. This is where your team's code repository will live.
- **Lesson: Using Git in the Real World** ➔ **[CRITICAL]** This teaches you **Feature Branching**. In a team of 4, no one should ever push code directly to the main branch. Your teammate writing C# will work on a backend branch, you will work on a frontend branch, and you will merge them together using **Pull Requests**.

🛑 What to Skim / Skip

- **Lesson: A Deeper Look at Git:** You can skim this quickly. It goes into the deep internal mechanics of how Git calculates file changes. It is interesting but won't change how you write code under a deadline.
- **Advanced Git Commands:** Avoid diving into complex commands like `git rebase`, `git cherry-pick`, or trying to fix detached heads. If your team runs into a Git error, it is much faster to just use a visual code editor tool (like Visual Studio Code's built-in Git manager) to resolve conflicts rather than mastering the command line versions.

💡 Pro-Tip for Your Team of 4

Since you are building a React frontend and your teammate is building an ASP.NET backend, create **two separate repositories on GitHub**:

1. `capstone-frontend` (Your React app)
2. `capstone-backend` (Their C# API)

Keeping them split prevents your frontend code updates from accidentally breaking their backend server setup and allows all 4 team members to work simultaneously without constantly running into messy merge conflicts.

---

Your Team's Daily Git Cheat Sheet

Here are the only **6 commands** your team needs to use every single day. Stick to this workflow to keep your code safe and avoid overwriting each other's work.

bash

```
# 1. Start your workday by pulling down any changes your team made
git pull origin main

# 2. Create a new "branch" for the specific feature you are building
git checkout -b feature-login-page

# 3. Check what files you have changed/added
git status

# 4. Stage your files to be saved
git add .

# 5. Save your changes locally with a descriptive message
git commit -m "Added login form UI and input validation"

# 6. Push your branch to GitHub so your team can review it
git push origin feature-login-page

# Once pushed, go to GitHub.com and open a Pull Request (PR) to merge your feature branch into the main branch.
```

---

How to Test and Run Split Repositories

It is a very common misconception that code has to live in the same folder to work together. Because your project uses a **Decoupled Architecture**, the two applications do not care where their code files live on your computer. They only care about communicating over your local network using internet protocols.

Think of it like this: Your teammate's backend is a **digital restaurant kitchen**, and your React frontend is a **waiter**. The waiter doesn't live inside the kitchen; they just talk to each other across the counter.

Here is exactly how you test and run them together locally on your machine:

Step 1: Run Both Servers Simultaneously

To test the full application, you will open **two separate terminal windows** on your computer:

1. **Terminal 1 (Backend):** Navigate to the backend folder and run the C# server. It will boot up and host an API locally, usually at an address like `https://localhost:5001`.
2. **Terminal 2 (Frontend):** Navigate to your React folder and run your development server (usually `npm run dev`). It will spin up your UI at a separate address, like `http://localhost:5173`.

Both servers run at the same time on your machine, utilizing different network "ports" (the numbers at the end of the address).

Step 2: Connect React to the C# API

Inside your React code, whenever you need data (like a list of users or products), you will point your JavaScript `fetch()` or `Axios` calls directly to your teammate's local backend address:

javascript

```
// Example of your React code fetching data from the C# server
useEffect(() => {
  fetch('https://localhost:5001/api/products') // Your partner's local C# endpoint
    .then(response => response.json())
    .then(data => setProducts(data));
}, []);
```

Step 3: Enable CORS (Crucial!)

By default, web browsers block a frontend running on port `5173` from stealing data from a backend running on port `5001` for security reasons.

To fix this so you can test smoothly, **your C# teammate must add a Cross-Origin Resource Sharing (CORS) policy** in their backend `Program.cs` file. This tells the C# server: _"It is safe to trust and give data to the React app running at http://localhost:5173."_

Step 4: Deploying to Production (The End Goal)

When it is time to hand in your capstone, you will host them in two different places on the internet:

- The C# backend will be hosted on a cloud platform (like Azure or Render). It will get a live URL like `https://yourcapstone.com`.
- Your React frontend will be hosted on a frontend platform (like Vercel or Netlify). It will get a live URL like `https://yourcapstone.com`.

You will simply change the fetch URL in your React code from `localhost` to the live backend URL, and everything will work seamlessly.

---
#### React Course

Here is the exact map of your React curriculum. Based on the syllabus you provided, you can completely **cross out 11 lessons and projects**.

Focus strictly on the **Core Fundamentals** and **The React Ecosystem** sections, as those contain the exact mechanics you need to connect your frontend to the ASP.NET backend.

---

🟢 INCLUDE: Core Fundamentals (Do These in Order)

These lessons teach you how React works, how it tracks data, and how it updates the user interface.

- **Introduction To React**
- **Setting Up A React Environment** _(Note: Choose **Vite** if the lesson gives you a choice between Vite and Create React App)._
- **React Components**
- **What Is JSX?**
- **Passing Data Between Components** _(This teaches you "Props")._
- **Rendering Techniques** _(This teaches you conditional formatting like `if/else` in UI)._
- **Keys In React** _(Crucial for loop-rendering arrays of data)._
- **Introduction To State**
- **More On State**

🔵 INCLUDE: The Bridge to Your Capstone (Crucial)

These lessons are the most important part of the course for your specific project. They teach you how to create multiple pages (Routing) and how to talk to your partner's C# server.

- **How To Deal With Side Effects** _(This teaches you the `useEffect` hook)._
- **React Router** ➔ **[CRITICAL]** Your capstone will need multiple pages (e.g., a Home page, a Login page, a Dashboard). React Router is how you build a multi-page app.
- **Fetching Data In React** ➔ **[THE MOST CRITICAL LESSON]** This is exactly where you learn how to hook up your React frontend to your partner's ASP.NET API endpoints.
- **Styling React Applications** _(Skim this quickly just to pick a method—like standard CSS Modules or Tailwind—to make your app look presentable)._

---

🛑 EXCLUDE: Skip Completely to Save Time

- **Project: CV Application** & **Project: Memory Card**
    - _Why:_ Skip these portfolio projects. Instead, use that time to start building your actual capstone project layout using fake data.
- **Class Based Components** & **Component Lifecycle Methods**
    - _Why:_ This is the outdated 2019 way of writing React. Modern apps use Functional Components and Hooks. Learning this will only confuse you before January.
- **Introduction To React Testing** & **Mocking Callbacks And Components**
    - _Why:_ Automated testing is a luxury you do not have time for on a strict 2-month deadline. Manual testing (clicking your app to see if it works) is enough for a student capstone.
- **Project: Shopping Cart**
    - _Why:_ This is a massive capstone-level project within The Odin Project itself. Building it will eat up 2 to 3 weeks of your time. Skip it and move directly to your school capstone.
- **Managing State With The Context API**, **Reducing State**, & **Refs And Memoization**
    - _Why:_ These are advanced optimization tools. For your project, standard React `useState` passed down through props is perfectly sufficient and much simpler to debug.

---

Would you like me to generate that **C# CORS code snippet** for your teammate now so you can drop it into your group chat and check it off your list?