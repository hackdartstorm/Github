# 🚀 Git & GitHub — A Beginner's Survival Guide

> Learn Git the fun way — with emojis, simple words, and zero confusion. 🎯

![Git](https://img.shields.io/badge/Git-F05032?style=for-the-badge&logo=git&logoColor=white)
![GitHub](https://img.shields.io/badge/GitHub-181717?style=for-the-badge&logo=github&logoColor=white)
![License](https://img.shields.io/badge/License-MIT-yellow?style=for-the-badge)
![Contributions Welcome](https://img.shields.io/badge/contributions-welcome-brightgreen?style=for-the-badge)
![Beginner Friendly](https://img.shields.io/badge/beginner--friendly-green?style=for-the-badge)

<div align="center">

[📚 Documentation](docs/) • [🤝 Contributing](CONTRIBUTING.md) • [📜 Code of Conduct](CODE_OF_CONDUCT.md) • [🐛 Report Issue](https://github.com/hackdartstorm/Github/issues)

</div>

---

## 📑 Table of Contents

1. [Repository Initialization](#-1-the-birth-of-a-repo-initialization)
2. [File States](#-2-the-life-cycle-of-a-file-file-states)
3. [Commits](#-3-commits-the-checkpoints)
4. [Git Status & Symbols](#-4-git-status--symbols)
5. [Git Reset](#-5-undo-changes-git-reset)
6. [Git Stash](#-6-git-stash-the-pause-button)
7. [Branching](#-7-branching-parallel-universes)
8. [Quick Reference](#-quick-reference)

---

## 🐣 1. The Birth of a Repo: Initialization

This is where it all begins.

**Concept:**
**`git init`** means "Start tracking this folder with Git." It turns a normal folder into a Git repository by creating a hidden `.git` folder inside.

```bash
git init
```

---

## 📂 2. The Life Cycle of a File (File States)

Git doesn't automatically save every change you make. Files go through specific "zones" before they are permanently saved.

### 1️⃣ Untracked Files

👉 **Git is saying:**
> "I see this file in the folder, but you never told me to track it. If you delete it, I can't help you."

**Action:** Move it to the staging area (start tracking):

```bash
git add notes.txt
```

### 2️⃣ Modified (Unstaged)

👉 **Git is saying:**
> "You changed this file, but you haven't chosen to include these specific changes in the next snapshot yet."

**Action:** Move the changes to the staging area:

```bash
git add notes.txt
```

### 3️⃣ Staged (Ready to Commit)

👉 **Git is saying:**
> "Cool, I've noted these changes. They are packed and ready to be saved in the next version."

**Action:** Save it permanently:

```bash
git commit -m "Update app logic"
```

---

## 📸 3. Commits: The Checkpoints

Think of a commit as a **save point** in a video game. If you mess up later, you can always go back to this point.

### Setting a Checkpoint

```bash
git add .
git commit -m "Checkpoint: login feature working"
```

> 💡 **Note:** `-m` means "message". That commit becomes a restore point you can return to anytime.

### Viewing All Checkpoints

```bash
git log --oneline
```

**Example Output:**
```text
a3f9c1d Add login validation
8b21e7a Checkpoint: login feature working
4d8a1ff Initial project setup
```

Each line = one checkpoint. ✨

---

## 🕵️ 4. Git Status & Symbols

Checking `git status` tells you what state your files are in.

### Long Version (Wordy)

```bash
git status
```

**Output:**
```text
modified:   notes.txt
untracked files:
    notes.txt
```

### Short Version (Clean)

```bash
git status -s
```

**Output:**
```text
 M notes.txt
?? notes.txt
```

### Decoding the Symbols

| Symbol | Location | Meaning | Explanation |
| :---: | :--- | :--- | :--- |
| `??` | Working folder | **Untracked** | File exists but Git is not tracking it |
| `M` | Either column | **Modified** | File was modified |
| `A` | Staging area | **Added** | New file staged for commit |
| `D` | Either column | **Deleted** | File was deleted |

### Common Scenarios

| Symbol | Meaning | What Happened |
| :---: | :--- | :--- |
| `?? notes.txt` | Untracked | You haven't run `git add` yet |
| `M notes.txt` | Modified | You edited the file, but didn't add it yet |
| `M  notes.txt` | Staged | You ran `git add notes.txt` — ready to commit |
| `MM notes.txt` | Staged + Modified | You staged one version, then changed it again |
| `A  notes.txt` | Added | Brand new file added to staging |
| `D notes.txt` | Deleted | Deleted in working folder, not staged yet |

---

## ⏪ 5. Undo Changes: Git Reset

Sometimes we make mistakes. `git reset` helps us go back in time.

**Command Structure:** `git reset [mode] [commit-hash]`

### Reset Modes Comparison

| Mode | Command | What Happens? | Danger Level |
| :--- | :--- | :--- | :---: |
| **Soft** | `git reset --soft HEAD~1` | Undoes the commit, but **keeps your changes** in the Staging Area | 🟢 Safe |
| **Mixed** | `git reset HEAD~1` | Undoes the commit and **unstages changes**, but keeps the code | 🟡 Medium |
| **Hard** | `git reset --hard HEAD~1` | **Destroys everything** — undoes commit and deletes changes | 🚨 **DANGER** |

### Detailed Breakdown

#### 🔹 Soft Reset
```bash
git reset --soft <commit>
```
**Use when:** You only want to undo the commit, not the work.

- ✅ `HEAD` moves back
- ✅ Commit is undone
- ✅ All changes stay **STAGED**
- ✅ Nothing deleted

> 👉 **Meaning:** "Undo the commit, keep everything ready to commit again."

#### 🔹 Mixed Reset (Default)
```bash
git reset --mixed <commit>
# or simply:
git reset <commit>
```
**Use when:** You want to undo the commit and re-choose what to add.

- ✅ `HEAD` moves back
- ✅ Commit is undone
- ✅ Files become **MODIFIED** (unstaged)
- ✅ Nothing deleted

> 👉 **Meaning:** "Undo the commit, but unstage the files so I can edit/select again."

#### 🔹 Hard Reset
```bash
git reset --hard <commit>
```
**Use when:** You want to completely go back and erase everything after that point.

- ✅ `HEAD` moves back
- ❌ Staging area cleared
- ❌ Working files reset
- ❌ All changes after that commit **DELETED**

> 👉 **Meaning:** "Go back exactly to that version and delete all later work."

### 🪄 Magic Recovery Trick

Lost a commit? Use `git reflog` to find it!

```bash
git reflog
```

**Example Output:**
```text
f3a9c1d HEAD@{0}: reset: moving to B
9ab21e4 HEAD@{1}: commit: Safety checkpoint before experiment
```

That second line is your lost commit! Bring it back:

```bash
git reset --hard 9ab21e4
```

**Boom!** 💥 Checkpoint restored.

---

## 📦 6. Git Stash: The "Pause" Button

### Scenario
You're working on a messy new feature, but your boss asks you to fix a bug on the main code immediately. You aren't ready to commit yet.

### Solution: Stash It!
Put your changes in a temporary drawer.

```bash
git stash
```

**What it saves:**
- Modified tracked files
- Staged changes

Your folder goes back to the last commit state.

### Stash Commands

| Command | Description |
| :--- | :--- |
| `git stash` | Save changes temporarily |
| `git stash pop` | Bring changes back and delete the stash |
| `git stash apply` | Bring changes back, keep the stash |
| `git stash list` | List all stashed items |
| `git stash drop stash@{0}` | Delete a specific stash |
| `git stash clear` | Delete all stashes |

### Apply Specific Stash

```bash
git stash apply stash@{1}
```

Your work returns, but the stash still exists. 🎯

---

## 🌿 7. Branching: Parallel Universes

Branching allows you to create a separate copy of your code to experiment without breaking the main project.

### Branch Commands

| Goal | Command |
| :--- | :--- |
| **Create a branch** | `git branch feature-login` |
| **View all branches** | `git branch` |
| **Switch to branch** | `git switch feature-login` <br> *(or `git checkout feature-login`)* |
| **Create & Switch** | `git switch -C feature-login` <br> *(or `git checkout -b feature-login`)* |
| **Merge branch** | `git merge feature-login` (run from `main`) |
| **Delete a branch** | `git branch -d feature-login` |

### Visual Flow

```text
main:     o───o───o───o
           \
feature:    o───o───o
```

---

## 📋 Quick Reference

### Daily Workflow

```bash
# 1. Start tracking a new file
git add <filename>

# 2. Stage all changes
git add .

# 3. Commit with a message
git commit -m "Your message here"

# 4. Check status
git status -s

# 5. View commit history
git log --oneline
```

### Undo Operations

```bash
# Undo last commit, keep changes staged
git reset --soft HEAD~1

# Undo last commit, unstage changes
git reset HEAD~1

# Undo everything (DANGEROUS!)
git reset --hard HEAD~1

# Recover lost commits
git reflog
```

### Branch Operations

```bash
# Create and switch to new branch
git switch -C <branch-name>

# Merge branch into current
git merge <branch-name>

# Delete a branch
git branch -d <branch-name>
```

### Stash Operations

```bash
# Save work for later
git stash

# Restore work
git stash pop

# List stashes
git stash list
```

---

## 🎓 Pro Tips

1. **Commit often** — Small commits are easier to manage
2. **Write clear messages** — Future you will thank you
3. **Use branches** — Never work directly on `main` for new features
4. **Check status** — Run `git status` before and after commands
5. **Use reflog** — It's your safety net for lost commits

---

## 📄 License

This project is licensed under the [MIT License](LICENSE).

---

## 🌟 Community

### 🤝 Contributing

We welcome contributions from everyone! Whether it's fixing a typo, adding new content, or suggesting improvements — your help is appreciated.

- 📖 Read our [Contributing Guide](CONTRIBUTING.md)
- 🐛 Report bugs via [Issues](https://github.com/hackdartstorm/Github/issues)
- 💡 Suggest features via [Issues](https://github.com/hackdartstorm/Github/issues)
- 🔀 Submit [Pull Requests](https://github.com/hackdartstorm/Github/pulls)

### 📢 Connect

- 💬 Start a [Discussion](https://github.com/hackdartstorm/Github/discussions)
- ⭐ Star this repo if you found it helpful!

---

## 🙏 Acknowledgments

Thank you to all the contributors who help make this guide better for beginners everywhere!

<a href="https://github.com/hackdartstorm/Github/graphs/contributors">
  <img src="https://contrib.rocks/image?repo=hackdartstorm/Github" alt="Contributors" />
</a>

---

<p align="center"><strong>Happy Coding!</strong> ✨</p>
