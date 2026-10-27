
2025-09-14  19:02

Tags: [[Terminal]], [[Git]], [[Github]], [[Coding]], [[The Odin Project]]

---

# Git Commands


## Workflow

**1.Update Your Main Branch:** Prerequisite before creating new work.

Ensure your local `main` (or `master`) branch is up to date with the remote repository before branching off:
```bash
# Switch to the main branch
git switch main

# Pull the latest remote changes
git pull origin main
```

**2.Create and Switch to Feature Branch:** Uses git switch -c.

Create a new feature branch and immediately jump into it using the `-c` (create) flag:
```bash
# Create and switch to a new branch named 'feature/user-auth'
git switch -c feature/user-auth
```

_Tip:_ To base your new branch off a specific commit or remote branch rather than `HEAD`, append it to the command: `git switch -c feature/user-auth origin/main`

**3.Work and Commit Changes:** Isolated development.

Stage and commit your changes as you build the feature:
```bash
# Check affected files
git status

# Stage changes
git add .

# Commit changes
git commit -m "feat: add user login form"
```

**4.Push to remote and process the pull request on Github**

```bash
git push
```

**5.Switch Back to Main Branch and pull from remote**

Once your work is committed, switch back to your main branch and do pull from remote:
```bash
git switch main
git pull
```

_Tip:_ Use `git switch -` as a quick shortcut to toggle back to your **previous** branch.

**6.Delete the Feature Branch:** Requires git branch -d or -D.

`git switch` handles navigation, but branch deletion is still handled by `git branch`. You cannot delete a branch while you are currently on it.
```
# Safe delete (fails if branch has unmerged commits)
git branch -d feature/user-auth

# Force delete (discards unmerged commits permanently)
git branch -D feature/user-auth
```


---
## Command Cheat Sheet

| **Task**                            | **Modern Command (git switch)** |
| ----------------------------------- | ------------------------------- |
| **Switch to existing branch**       | `git switch <branch>`           |
| **Create and switch to branch**     | `git switch -c <branch>`        |
| **Switch back to previous branch**  | `git switch -`                  |
| **Fetch & switch to remote branch** | `git switch <remote-branch>`    |

---


This is a reference list of my most commonly used Git commands

Commands related to a remote repository:
- git clone git@github.com:USER-NAME/REPOSITORY-NAME.git
- git push or git push origin main (Both accomplish the same goal in this context)

Commands related to the workflow:
- git add .
- git commit -m "A message describing what you have done to make this snapshot different"

Commands related to checking status or log history
- git status
- git log (press q to escape)

Commands when git push does not work
- git pull origin main
- git push origin main

Add local repository to a newly-made remote repo from github
1. create repo from github
2. copy ssh
3. go to terminal and on repo folder
```bash
git add -A
git commit -m "initial commit"
git branch -M main
git remote add origin (ssh link)
git push -u origin main
```

Add unstaged to previous commit:
```
git commit --ammend
```


----

## Duplicate your own already-existing repository

```bash
create the new repo on github first and leave the repo empty (no readme, no license, etc)

# 1. Clone the original repository as a bare copy
git clone --bare https://github.com

# 2. Move into the bare repository directory
cd OLD-REPOSITORY-NAME.git

# 3. Mirror-push the contents into your new repository
git push --mirror https://github.com/new-repository-name

# 4. Remove the temporary local bare folder
cd ..
rm -rf OLD-REPOSITORY-NAME.git

git clone https//github.com/new-repository-name
```


---

The basic Git syntax is program | action | destination.

For example,
- git add . is read as git | add | ., where the period represents everything in the current directory;
- git commit -m "message" is read as git | commit -m | "message"; and
- git status is read as git | status | (no destination).

---

## Git Repo Setup

Permanently skip --set-upstream when pushing on branches, enter this:
```bash
git config --global push.autoSetupRemote true
```

Permanently clear a deleted branch from remote to local automatically:
```bash
git config --global fetch.prune true
```

---
# References

Odin Project - Foundations
Gemini/Claude