
2026-06-25  12:49 am

Tags: [[Job]]

---
# Linewise Data Annotation Notes


# Module 1

- Contact-based = strict ±5 frames. 
- Intent-based = subjective, but place the new label BEFORE the next contact.

- 3-action bundle (only if all are very brief). 
- Cyclic tasks capped at 10s. 
- Idle ends at first movement, not first contact.


# Module 2

- Sentence structure - https://www.youtube.com/watch?v=yjweFUW6Hb8
![[Screenshot from 2026-06-25 00-58-07.png]]
- Imperative form. 
- Self-contained. 
- Only physical hand-object actions. 
- Only the ego, only in frame.


# Module 3
### Banned verbs
Verb choice - https://youtu.be/THGGVS6633c?si=6e0X9Ok7P7PKFfDe
![[Screenshot from 2026-06-25 01-03-23.png]]

These verbs are **never** allowed in T2 labels. There are three categories:
#### 1. Intention verbs (describe thinking, not doing)
- analyze, arrange, assess, browse, check, choose, compare, confirm, count, ensure, examine, inspect, look, match, measure, monitor, observe, organize, prepare, reach for, refine, review, rummage, search, select, survey, test, verify, view, weigh

#### 2. Sequence verbs (describe order, not action)
- begin, complete, continue, finalize, finish, first, initiate, maintain, rearrange, start

#### 3. Vague action verbs (too general)
- assemble, fix, handle, manipulate, pace, perform, section, work

Fail - Inspect the apple with the right hand. _(intention verb)_
Fail - Continue scrubbing the pan with the left hand. _(sequence verb)_
Fail - Manipulate the pan under the faucet. _(vague action verb)_

- If a verb is conditional, the condition must be visible in the label. If you can't satisfy the condition, pick a different verb.

- Every meaningful hand action specifies a hand. 
- "Both hands" = same action by both. Different roles = describe each. 
- Order matters. 
- Ignore non-task hands.


# Module 5

- Object description (not in ppt) - https://youtu.be/X_iOwovEiz0?si=6wOH0mzU8v9J3SoX
![[Pasted image 20260625011744.png]]
![[Pasted image 20260625011809.png]]

- Specific noun > generic. 
- Disambiguate 2–3 similar objects. 
- Avoid banned modifiers - `additional, again, another, current, extra, final, further, more, new, old, other, remaining, specific`
- Conditional nouns need qualifiers.


# Module 6

- Egocentric by default. 
- To use the object's own orientation, append (O) right after the direction word. 
- Pick whichever stays clearer across the segment.

### When and how to use (O)

By default, all directions in a label are **egocentric** — from the ego's point of view.

Sometimes the object has its own orientation that matters — like a shirt that's been laid out, or a tool that's been rotated. In that case, you can describe directions from the **object's own perspective** by appending `(O)` immediately after the direction word.

#### Example: a shirt on a table

Picture a shirt laid flat on a table. The shirt's **collar points to the LEFT side of the frame**, and the hem points to the right. The ego grabs the collar with their right hand.

Pass — egocentric: Grab the left side of the shirt with the right hand. _(from ego's POV, the collar is on the left)_

Pass — object-centric: Grab the top (O) of the shirt with the right hand. _(from the shirt's own orientation, the collar is the top)_

Both labels are acceptable. The annotator picks whichever keeps the meaning clear.

#### When object-centric is better

Object-centric is often clearer when:

- The object rotates during the segment (egocentric directions would shift mid-action)
- The object has an unambiguous "top," "front," "bottom," etc. (like clothing, vehicles, tools)
- You need a stable referent across multiple segments

#### Critical rule: tag it

If you're using an object-centric direction, you **must** mark it with `(O)`. An unmarked object-centric direction is treated as egocentric, which means the label says something different from what you intended.

FailGrab the top of the shirt with the right hand. _(when "top" means the shirt's collar, but it's unmarked — reader assumes egocentric "top")_


# Module 7

- Run every label through the 7-point checklist before submitting. 
- Catching your own mistakes is faster than getting recalled by FQC.

![[Pasted image 20260625012806.png]]

### Self-review checklist and common mistakes

Before you submit any annotation, walk through this checklist for each label:

1. **Form**: Is it an imperative command (not -ing, not "begin/finish")?
2. **Verbs**: Any banned verbs? Are conditional verbs used correctly (with destination, paired action, etc.)?
3. **Nouns**: Are objects specific? Are 2–3 similar objects disambiguated? Any banned modifiers ("another", "more", "remaining")?
4. **Hands**: Is each meaningful hand action attributed? Is "both hands" only used when correct? Is the order correct?
5. **Perspective**: If using object-centric directions, are they tagged with (O)?
6. **Self-contained**: Does the label stand alone, without referencing other segments?
7. **Reality check**: Does it match what's actually happening in the video? No intentions, no out-of-frame, no non-ego actions?

#### Most common mistakes (in order)

1. Banned intention verbs: "inspect", "check", "look at"
2. "Manipulate" used as a generic verb
3. Conditional verbs missing their condition: "move X" (no destination), "use X" (no paired verb)
4. Missing object disambiguation when multiple similar objects are visible
5. "Both hands" used when only one hand is task-relevant
6. Order of operations error in two-handed sequential actions
7. Object-centric directions without (O) marker


Submission ID: VL-MQSD5GS8