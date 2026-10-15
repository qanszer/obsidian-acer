
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
- Creation of a classroom can only be done if you have an account


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

### Database

User
- user ID
- name (nullable)
- email (nullable)
- is anonymous
- created at

Classroom
- classroom ID
- 4-letter join code (unique)
- name/subject
- owner user ID (FK → User)
- active/archived status

Membership          (also create a row for the owner)
- user ID (FK → User)
- classroom ID (FK → Classroom)
- joined at          (classroom sort: newest/oldest)
- sort order         (NEW, manual drag)
- is blocked

Question
- question ID
- classroom ID (FK → Classroom)
- author user ID (FK → User)
- question text
- timestamp submitted
- edited at (nullable)          (NEW)
- deleted at (nullable)         (NEW, replaces status; powers the archive)
- deleted by (nullable)         (NEW, author / professor)

Upvote              (NEW)
- question ID (FK → Question)
- user ID (FK → User)
- primary key: (question ID, user ID)

---

## Tasks

- finish all the screens
- add room implementation to all screens
- duplicate the repo and name it `askly-application`
- change from room to firebase


---

## Color Scheme

```css
:root {
  --background: #f2f2f4;
  --foreground: #111113;
  --card: #ffffff;
  --card-foreground: #111113;
  --primary: #111113;
  --primary-foreground: #ffffff;
  --muted: #e6e6ea;
  --muted-foreground: #8e8e93;
  --accent: #111113;
  --accent-foreground: #ffffff;
  --border: #e3e3e8;
  --ring: #111113;
  --radius: 14px;
}

html.dark {
  --background: #0c0c0d;
  --foreground: #f4f4f6;
  --card: #1a1a1c;
  --card-foreground: #f4f4f6;
  --primary: #f4f4f6;
  --primary-foreground: #0c0c0d;
  --muted: #232326;
  --muted-foreground: #8e8e93;
  --accent: #f4f4f6;
  --accent-foreground: #0c0c0d;
  --border: #2a2a2e;
  --ring: #f4f4f6;
}

@theme inline {
  --color-background: var(--background);
  --color-foreground: var(--foreground);
  --color-card: var(--card);
  --color-card-foreground: var(--card-foreground);
  --color-primary: var(--primary);
  --color-primary-foreground: var(--primary-foreground);
  --color-muted: var(--muted);
  --color-muted-foreground: var(--muted-foreground);
  --color-accent: var(--accent);
  --color-accent-foreground: var(--accent-foreground);
  --color-border: var(--border);
  --color-ring: var(--ring);
  --font-serif: 'Plus Jakarta Sans', system-ui, sans-serif;
  --font-sans: 'Plus Jakarta Sans', system-ui, sans-serif;
}
```

**Surfaces**
Variable 	        Light	        Dark     Used for
--background	 #f2f2f4   #0c0c0d	App background
--card	         #ffffff 	#1a1a1c	Cards, sheets, inputs
--muted	     #e6e6ea	 #232326	Pressed and hover fills, segmented control track

**Text**
Variable	                     Light	     Dark	    Used for
--foreground	             #111113	#f4f4f6	Main text
--card-foreground	     #111113	#f4f4f6	Text on cards
--muted-foreground	#8e8e93	#8e8e93	Secondary text, hints, timestamps

**Actions**
Variable	                     Light	     Dark	    Used for
--primary	                 #111113	#f4f4f6	Main buttons, join code card
--primary-foreground	#ffffff   	#0c0c0d	Text and icons on primary
--accent	                 #111113	#f4f4f6	Toggles, checkboxes, selected states, warnings
--accent-foreground	#ffffff	    #0c0c0d	Text and icons on accent

**Lines and focus**
Variable	     Light	     Dark	    Used for
--border	#e3e3e8	#2a2a2e	Dividers, outlines, dashed empty states
--ring	     #111113	#f4f4f6	Keyboard focus ring


**Colours set directly in the code, outside the variables**
**Where	                                                             Value**
Bottom sheet backdrop	                                   black at 30% opacity
Phone frame shadow (wide screens)	               rgba(28,26,21,0.5)
Shadow on a classroom card while dragging	       rgba(28,26,21,0.35)
Google logo	                                       #EA4335, #4285F4, #FBBC05, #34A853
Theme preview tiles in Settings  #f4f1ea, #16140f, #1c1a15, #efe9dc, #b3512d

---

## Fonts

**Font Sizes**
1. Small - 14px
2. Default - 16px
3. Large - 18.5px

**Fonts**
Plus Jakarta Sans, system-ui, sans-serif


---

Askly
Submit questions anonymously during a lecture. Ask without raising a hand.


```kotlin
@Composable
fun CustomScreenWithoutScaffold() {
    // Root container filling full screen + handling system status/navigation bars
    Column(
        modifier = Modifier
            .fillMaxSize()
            .systemBarsPadding() // Ensures content doesn't get cut off by status/nav bar
    ) {
        // 1. CUSTOM TOP BAR (Fixed at very top)
        Row(
            modifier = Modifier
                .fillMaxWidth()
                .height(56.dp)
                .background(MaterialTheme.colorScheme.surfaceVariant)
                .padding(horizontal = 16.dp),
            verticalAlignment = Alignment.CenterVertically
        ) {
            Text(
                text = "My Custom TopBar",
                style = MaterialTheme.typography.titleMedium
            )
        }

        // 2. MIDDLE CONTENT (Pushed closer to the top)
        Column(
            modifier = Modifier
                .fillMaxWidth()
                .weight(1f) // Takes up all remaining space, pushing bottom content down
                .padding(16.dp),
            verticalArrangement = Arrangement.Top // Ensures content stays near top
        ) {
            Text(
                text = "Upper Content",
                style = MaterialTheme.typography.headlineSmall
            )
            Spacer(modifier = Modifier.height(8.dp))
            Text(
                text = "This content stays near the top section of the screen.",
                style = MaterialTheme.typography.bodyMedium
            )
        }

        // 3. TWO CARDS AT THE VERY BOTTOM
        Row(
            modifier = Modifier
                .fillMaxWidth()
                .padding(16.dp),
            horizontalArrangement = Arrangement.spacedBy(12.dp) // Gap between cards
        ) {
            // Card 1 (flex-grow: 1)
            Card(
                modifier = Modifier
                    .weight(1f)
                    .height(100.dp)
            ) {
                Box(
                    modifier = Modifier.fillMaxSize(),
                    contentAlignment = Alignment.Center
                ) {
                    Text("Card 1")
                }
            }

            // Card 2 (flex-grow: 1)
            Card(
                modifier = Modifier
                    .weight(1f)
                    .height(100.dp)
            ) {
                Box(
                    modifier = Modifier.fillMaxSize(),
                    contentAlignment = Alignment.Center
                ) {
                    Text("Card 2")
                }
            }
        }
    }
}
```


---

## Branches

 1. Start with foundations (Auth & Settings)
- git switch -c feature/ui-auth-nav /
- git switch -c feature/ui-settings

 2. Build Student Flow
- git switch -c feature/ui-student-dashboard /
- git switch -c feature/ui-student-questions 

 2. Build Professor Flow
- git switch -c feature/ui-prof-dashboard
- git switch -c feature/ui-prof-questions

 4. Finish with Shared Screens
- git switch -c feature/ui-archive


---

## Boilerplate

```kotlin
val context = LocalContext.current;  
  
Column(  
    modifier = Modifier  
        .fillMaxSize()  
        .systemBarsPadding()  
) {  
    // Custom Top Bar  
    Column(  
        modifier = Modifier  
            .padding(horizontal = 10.dp)  
            .fillMaxWidth(),  
        verticalArrangement = Arrangement.Center  
    ) {  
        Row(  
            modifier = Modifier  
                .fillMaxWidth(),  
            verticalAlignment = Alignment.CenterVertically,  
            horizontalArrangement = Arrangement.SpaceBetween  
        ) {  
            
        }
	}  
        
    // Content Area  
    Column() {
	    
	}
	  
    // Bottom Bar  
    Button() {
	   
	}    
	Spacer( modifier = Modifier.height(20.dp))  
}
```