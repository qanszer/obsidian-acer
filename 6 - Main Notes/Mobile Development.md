
2026-09-18  10:26pm

Tags: [[School]], [[Coding]], [[Kotlin]]

---
# Mobile Development


## Local Database Setup Using Room Feature (Manual)

1. Copy paste this under build.gradle.kts > dependencies
```kotlin
implementation("androidx.room:room-runtime:2.8.5")  
implementation("androidx.room:room-ktx:2.8.5")  
ksp("androidx.room:room-compiler:2.8.5")
```
- the version here depends on your kotlin version which can be seen on libs.versions.toml > versions > kotlin
- use ai to know the right code to copy paste for your version, in this case this works on version 2.2.10


---

## 10/3/26 - Firebase Database

Agendas
- Database schema
- Github integration

```
implementation("androidx.lifecycle:lifecycle-viewmodel-compose:2.8.7)
```


---

## Frontend of Kotlin using Jetpack Compose

### 1. The "Divs" of Compose: The Big Three

In web development, you might use a generic `<div>` and assign it `display: flex`. In Compose, you declare the directional flow of your layout upfront using one of three core container functions.

|**Compose Layout**|**CSS Equivalent**|**What it does**|
|---|---|---|
|`Row { ... }`|`display: flex; flex-direction: row;`|Places items horizontally, side-by-side.|
|`Column { ... }`|`display: flex; flex-direction: column;`|Places items vertically, stacked top to bottom.|
|`Box { ... }`|`position: absolute/relative;`|Overlaps elements on top of each other (Z-axis).|

### 2. Main Axis and Cross Axis (Alignment vs. Arrangement)

Flexbox uses `justify-content` for the main axis and `align-items` for the cross axis. Compose uses the exact same concept, mapping them to **Arrangement** and **Alignment**.

**For a `Row` (Main axis: Horizontal, Cross axis: Vertical):**

- `horizontalArrangement` (CSS: `justify-content`)
    
    - `Arrangement.Start` (CSS: `flex-start`)
        
    - `Arrangement.Center` (CSS: `center`)
        
    - `Arrangement.SpaceBetween` (CSS: `space-between`)
        
    - `Arrangement.SpaceEvenly` (CSS: `space-evenly`)
        
- `verticalAlignment` (CSS: `align-items`)
    
    - `Alignment.Top` (CSS: `flex-start`)
        
    - `Alignment.CenterVertically` (CSS: `center`)
        
    - `Alignment.Bottom` (CSS: `flex-end`)
        

**For a `Column` (Main axis: Vertical, Cross axis: Horizontal):**

- `verticalArrangement` handles the vertical spacing (`justify-content`).
    
- `horizontalAlignment` handles the horizontal positioning (`align-items`).
    

### 3. Modifiers: Your CSS Stylesheet

In the DOM, you apply styles via a `class`. In Compose, you pass a `Modifier` object to your UI elements. Modifiers are chained sequentially, and **order matters critically**—each modifier wraps the previous one.

- **Sizing (Width/Height):**
    
    - `Modifier.fillMaxWidth()` acts like `width: 100%;`
        
    - `Modifier.fillMaxSize()` acts like `width: 100%; height: 100%;`
        
    - `Modifier.size(100.dp)` acts like `width: 100px; height: 100px;` (Note: Android uses `dp` (density-independent pixels) instead of `px` to account for varying screen pixel densities).
        
- **Flex-Grow:** To make an element expand to fill all remaining available space inside a `Row` or `Column`, use `Modifier.weight(1f)`. This is the exact equivalent of `flex-grow: 1`.
    
- **Margin vs. Padding:** Compose does not have a distinct "margin" property. Instead, you use `padding` relative to when you draw your background. Applying padding _before_ a background acts like CSS margin, while applying it _after_ acts like CSS padding.

```kotlin
// CSS equivalent: margin: 16px; background-color: blue; padding: 8px;
Text(
    text = "Hello World",
    modifier = Modifier
        .padding(16.dp) // Acts as Margin (applied outside the background)
        .background(Color.Blue)
        .padding(8.dp)  // Acts as Padding (applied inside the background)
)
```

### 4. Translating a Figma Mockup

To build any screen from a Figma file, you don't need absolute positioning. You simply draw imaginary bounding boxes and break the UI down into recursive rows and columns:

1. **The Root Level:** Most screens are a vertical flow of sections. Start with a `Column`. If the screen needs to scroll (CSS `overflow-y: scroll`), you would use a `LazyColumn` (for long dynamic lists) or add `Modifier.verticalScroll(...)` to a standard `Column`.
    
2. **Section by Section:** Look at a single component, like a user profile card. Does it have an avatar on the left and text on the right? That’s a `Row`.
    
3. **Stacking Text:** Inside that `Row`, the user's name is usually placed directly above their bio. That means the text section is a `Column` nested inside the `Row`.
    
4. **Floating/Overlapping Elements:** If a floating action button is pinned over the bottom of a scrolling list, or a red notification badge overlaps a bell icon, wrap both in a `Box` and use `Modifier.align()` on the child element to pin it exactly where it belongs.