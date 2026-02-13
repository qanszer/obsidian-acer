
2026-02-13  04:43 pm

Tags: [[Coding]] [[Advice]] [[Guide]]

---
# Best Process for Making a Website

There's no single "correct" answer - it depends on your project, but here are the common approaches:

---

## **1. Front-End First (Most Common for Beginners & Small Projects)**

### Process:

1. Design the UI/layout (wireframes/mockups)
2. Build the HTML/CSS structure
3. Add interactivity with JavaScript
4. Build the backend to support what you've already created
5. Connect front-end to backend

### Pros:

- **Visual progress** - you see results immediately
- **Better user experience planning** - you think about UX early
- **Easier to demo** - stakeholders can see and give feedback
- **Clearer requirements** - you know exactly what the backend needs to do

### Cons:

- Might need to redesign if backend limitations arise
- Could waste time on features that are technically impossible

### Best for:

- Personal projects
- Portfolio websites
- Simple applications
- When you're learning
- Client projects (they can see progress)

---

## **2. Back-End First (Better for Complex Systems)**

### Process:

1. Plan database structure
2. Build API endpoints and business logic
3. Test with tools like Postman
4. Build front-end to consume the API

### Pros:

- **Solid foundation** - ensures technical feasibility
- **Easier to test** - backend logic tested independently
- **Multiple front-ends** - can build web, mobile, desktop from same backend
- **Better for teams** - frontend and backend devs can work in parallel

### Cons:

- No visual progress early on
- Harder to demo to non-technical people
- Might build features that aren't needed

### Best for:

- Large applications
- Apps with complex business logic
- When you need multiple platforms (web + mobile)
- Team projects
- Data-heavy applications

---

## **3. MVP Approach (Recommended for Most Projects)**

Build the **Minimum Viable Product** by doing a bit of both simultaneously:

### Process:

1. **Plan** - Define core features only
2. **Design** - Simple wireframes (not full design)
3. **Build vertical slice** - Pick ONE feature and build it fully (front + back)
4. **Test** - Make sure it works end-to-end
5. **Repeat** - Add features one at a time

### Example - Todo App:

- **Iteration 1**: Just display hardcoded todos (frontend only)
- **Iteration 2**: Add ability to create a todo (frontend + backend)
- **Iteration 3**: Add ability to delete (frontend + backend)
- **Iteration 4**: Add user authentication
- **Iteration 5**: Polish UI and styling

### Pros:

- Always have a working product
- Catch integration issues early
- Easy to pivot if needed
- Can release early and get feedback

---

## **4. The Realistic Modern Approach**

Here's what most developers actually do:

1. **PLANNING** (1-2 days)
	   - Sketch the main pages
	   - List required features
	   - Plan database structure roughly
2. **SETUP** (1 day)
	   - Set up project structure
	   - Choose tech stack
	   - Initialize both front and back
3. **BUILD CORE FEATURE** (frontend + backend together)
	   - Pick the most important feature
	   - Build the UI for it
	   - Build the API for it
	   - Connect them
	   - Test it works
4. **REPEAT** for each feature
	   - Add features one by one
	   - Always keep it working
5. **POLISH**
	   - Improve styling
	   - Add animations
	   - Optimize performance
	   - Fix bugs

---

## **My Recommendation Based on Your Situation:**

### **If you're learning:**

→ **Front-end first**

- See results quickly
- Understand what you're building
- Can use fake data initially
- More motivating

### **If it's a personal project:**

→ **MVP approach**

- Start simple
- Add features gradually
- Stay motivated with working product

### **If it's a professional project:**

→ **Backend first or simultaneous**

- Ensure technical feasibility
- Better planning
- Easier to maintain

---

## **Practical Example: Building a Blog**

### Front-End First Approach:

```
Day 1-2: Design all pages in HTML/CSS
Day 3: Add JavaScript for interactions
Day 4: Build backend API
Day 5: Connect frontend to backend
```

### MVP Approach:

```
Day 1: Design homepage + build API to fetch posts
Day 2: Design single post page + build API for one post
Day 3: Add create post page + build create API
Day 4: Add edit/delete + build those APIs
Day 5: Add authentication + secure APIs
```

---

## **Tools That Help:**

- **Wireframing**: Figma, Excalidraw
- **Backend testing**: Postman, Insomnia
- **Fake data**: JSONPlaceholder, Faker.js
- **Version control**: Git (commit working versions)

---
