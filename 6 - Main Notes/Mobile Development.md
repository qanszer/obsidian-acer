
2026-09-18  10:26pm

Tags: [[School]], [[Coding]], [[Kotlin]]

---
# Mobile Development


### Local Database Setup Using Room Feature (Manual)

1. Copy paste this under build.gradle.kts > dependencies
```kotlin
implementation("androidx.room:room-runtime:2.8.5")  
implementation("androidx.room:room-ktx:2.8.5")  
ksp("androidx.room:room-compiler:2.8.5")
```
- the version here depends on your kotlin version which can be seen on libs.versions.toml > versions > kotlin
- use ai to know the right code to copy paste for your version, in this case this works on version 2.2.10
- 