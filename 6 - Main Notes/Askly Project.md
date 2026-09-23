
2026-09-22  01:07pm

Tags: [[Coding]], [[School]], [[Kotlin]]

---
# Askly Project

This is a project for my Mobile Development class. 

Askly is an Android application designed to eliminate the barriers students face when asking questions during academic lectures. By providing a real-time, completely anonymous platform, Askly helps students voice their inquiries without the fear of judgment, stage fright, or forgetfulness. Professors can seamlessly manage incoming questions and address them at natural breaking points during their presentations.

## The Problem  

During traditional lectures, many students hesitate to raise their hands when a professor opens the floor for questions. This communication gap stems from:  
* Fear of being perceived as unintelligent by peers.  
* Discomfort speaking in front of a large audience or raising their voice.  
* A preference for complete anonymity.  
* Forgetting specific questions by the end of a long lecture segment.  
  
## The Solution  

Askly allows students to submit queries instantly and anonymously directly from their mobile devices. Professors receive these questions on a live dashboard, allowing them to review, address, and clear questions on the fly without interrupting the flow of the lecture.

---

## Features

**1.​ Professor Role**
- Can create a classroom (persistent data storage) with a generated 4-letter join code
- Can view the list of pending questions at any time
- Can remove a question from the list, typically after it has been answered
- Dashboard to view and select between classrooms
- Block a student from making questions using their question itself for identification
- Sort questions list (most upvoted is default, newest, oldest)
- Multiselect to delete questions or all questions
- Archive of deleted questions
- Multiselect option to leave classrooms or all
- Sort classrooms (manual drag, newest, oldest, a-z, z-a)

**2.​ Student Role**
- Can join a classroom using the professor's 4-letter code
- Can submit a question to the professor anonymously (limited characters)
- Can view their own submitted question(s) as well as other's anonymous questions
- Can remove their own question if it is answered or resolved before the professor opens the floor for questions
- Can edit their own question at any time
- Dashboard to view and select between classrooms
- Can upvote other existing questions
- Sort questions list (most upvoted is default, newest, oldest)
- Multiselect to delete questions or all own questions
- Archive of deleted questions
- Multiselect option to leave classrooms or all
- Sort classrooms (manual drag, newest, oldest, a-z, z-a)



- Settings feature for customization
	- adjust font size 
	- light and dark mode with different themes for each mode (w/ system default)
	- change default sort preference
	- spam threshold
	- turn on "are you sure?" popup
		- questions (off by default for individual, on for multiselect)
		- classrooms (default is on)


---

## The Major Competitors

|Platform|How it Works|Their Biggest Limitation|
|---|---|---|
|**[Slido](https://www.slido.com/)**|The industry giant. Students use a QR code or numeric link to join a session and type anonymous questions.|**Expensive / Restricted:** Their free plan limits the teacher to 3 polls, has a hard cap on participants, and **locks question moderation** behind a expensive paid tier.|
|**[Vevox](https://www.vevox.com/)**|Built specifically for university lectures. Anonymity is the default setting, and it integrates directly into Microsoft Teams and PowerPoint.|**Complex Interface:** It is designed for massive enterprises, meaning the setup and navigation can feel clunky and overwhelming for a quick lecture.|
|**[Mentimeter](https://www.mentimeter.com/)**|A presentation-first tool. Professors build slides, and students can submit questions anonymously at any time.|**Presentation Jail:** The Q&A feature is tied directly to their presentation software. If a professor wants to use local PDFs or live-code, Mentimeter doesn't adapt well.|
|**[QBox](https://play.google.com/store/apps/details?id=com.qbox.anonymousqa)**|A mobile app on the Google Play Store that functions identically to your concept—using 6-digit codes to join rooms.|**Feature Creep:** Focuses heavy attention on Google Sign-Ins and timing out rooms rather than a lightweight, student-first workflow.|

## How Askly Stands Out

1. **Zero Paywalls for Core Features:** Commercial apps like Slido make professors pay to moderate/delete inappropriate questions. **Askly gives professors full queue moderation** (viewing and removing questions) entirely for free. [[1](https://www.koji.so/blog/best-slido-alternatives-2026), [2](https://www.slido.com/features-live-qa)]
2. **Student-Controlled Mistake Correction:** On platforms like Slido, once a student hits "Submit," they cannot edit or delete their question. Askly’s **local-only authorization mechanism** allows anonymous students to edit or delete their own mistakes before the professor sees them. [[1](https://www.koji.so/blog/best-slido-alternatives-2026)]
3. **No-Friction Join Code:** Many alternatives use 5 to 6-digit room numbers or web links. Askly's choice of a short, easy-to-read **4-letter join code** makes it significantly faster for a student to punch into their phone at the back of a dark lecture hall. [[1](https://www.mentimeter.com/features/live-questions-and-answers), [2](https://play.google.com/store/apps/details?id=com.qbox.anonymousqa), [3](https://onlinequestions.org/)]

---

## How to Deploy and Concerns

### Method 1
The Easiest Way (GitHub Releases)

You compile the app in Android Studio, upload the installation file (`.apk`) to GitHub, and give users a download link.

1. **Build the APK in Android Studio:**
    - In the top menu, go to **Build** -> **Build Bundle(s) / APK(s)** -> **Build APK(s)**.
    - Wait a moment. When a notification pops up in the bottom right, click **locate** to find the file named `app-debug.apk` (or `app-release.apk`).
2. **Create a Release on GitHub:**
    - Go to your repository page on GitHub.
    - On the right-hand sidebar, click **Releases** -> **Create a new release**.
    - Set a version tag (like `v1.0.0`).
    - Drag and drop your `.apk` file into the binaries upload box.
    - Click **Publish release**.
3. **How users use it:**
    - You give them the link to your GitHub Releases page. They click the `.apk` file on their Android phone, download it, and install it instantly.

### Method 2
For Other Developers (Source Code)

If your target users are your classmates or professor who want to look at your code, they don't even need a download link.

1. They can simply open a terminal on their computer and run:
    
    bash
    
    ```
    git clone git@github.com:your-username/your-repo-name.git
    ```
    
    Use code with caution.
    
2. They open that cloned folder in Android Studio and run it on their own device or emulator.

---

### A Crucial Architecture Note

Your proposal states that the application works **"in real time"** and manages data for **Classrooms, Professors, and Questions** across different roles.

If you distribute the APK right now, **the app will only save data locally on that specific phone** unless you connect it to a shared cloud database (like Firebase Realtime Database or a Supabase backend). If a student submits a question on their phone, the professor will not see it on theirs unless both apps are talking to the same database over the internet.

---

