# 📚 Git Commands Cheat Sheet

A comprehensive reference for all Git commands covered in this guide.

---

## 🐣 Repository Setup

| Command | Description |
| :--- | :--- |
| `git init` | Initialize a new Git repository |
| `git clone <url>` | Clone a remote repository |
| `git remote -v` | View configured remotes |
| `git remote add origin <url>` | Add a remote repository |

---

## 📂 File Operations

| Command | Description |
| :--- | :--- |
| `git status` | Show working tree status |
| `git status -s` | Show short format status |
| `git add <file>` | Stage a file for commit |
| `git add .` | Stage all changes |
| `git add -p` | Stage changes interactively |
| `git rm <file>` | Remove file from tracking |
| `git mv <old> <new>` | Move or rename a file |
| `git checkout -- <file>` | Discard changes in working directory |

---

## 📸 Commits

| Command | Description |
| :--- | :--- |
| `git commit -m "msg"` | Commit with a message |
| `git commit -am "msg"` | Stage and commit in one step |
| `git commit --amend` | Modify the last commit |
| `git log` | View commit history |
| `git log --oneline` | View compact commit history |
| `git log --graph` | View history as a graph |
| `git log -n 5` | View last 5 commits |
| `git show <commit>` | Show details of a commit |

---

## 🌿 Branching

| Command | Description |
| :--- | :--- |
| `git branch` | List all branches |
| `git branch <name>` | Create a new branch |
| `git switch <branch>` | Switch to a branch |
| `git switch -C <name>` | Create and switch to branch |
| `git checkout <branch>` | Switch to a branch (legacy) |
| `git checkout -b <name>` | Create and switch (legacy) |
| `git merge <branch>` | Merge branch into current |
| `git branch -d <name>` | Delete a branch (safe) |
| `git branch -D <name>` | Delete a branch (force) |
| `git branch -m <new>` | Rename current branch |

---

## ⏪ Undo Changes

| Command | Description |
| :--- | :--- |
| `git reset --soft HEAD~1` | Undo commit, keep staged |
| `git reset HEAD~1` | Undo commit, unstage changes |
| `git reset --hard HEAD~1` | Undo commit, discard all |
| `git revert <commit>` | Create a new commit that undoes changes |
| `git reflog` | View reference log (recover lost commits) |

---

## 📦 Stashing

| Command | Description |
| :--- | :--- |
| `git stash` | Save changes temporarily |
| `git stash pop` | Apply and remove stash |
| `git stash apply` | Apply stash, keep it |
| `git stash list` | List all stashes |
| `git stash drop` | Delete a stash |
| `git stash clear` | Delete all stashes |
| `git stash show` | Show stash contents |

---

## 🔄 Remote Operations

| Command | Description |
| :--- | :--- |
| `git fetch` | Download objects from remote |
| `git pull` | Fetch and merge |
| `git push` | Upload changes to remote |
| `git push -u origin <branch>` | Push and set upstream |
| `git push --force` | Force push (use carefully!) |

---

## 🔍 Debugging

| Command | Description |
| :--- | :--- |
| `git blame <file>` | See who changed each line |
| `git diff` | Show unstaged changes |
| `git diff --staged` | Show staged changes |
| `git diff <branch1> <branch2>` | Compare two branches |
| `git log --author="name"` | Filter by author |
| `git log --since="2 weeks ago"` | Filter by date |

---

## ⚡ Pro Tips

```bash
# See all configured remotes
git remote -v

# Fetch all branches
git fetch --all

# Clean untracked files (DANGEROUS!)
git clean -fd

# Show current branch
git branch --show-current

# Count your commits
git rev-list --count HEAD
```

---

## 🎯 Common Workflows

### Starting a New Feature
```bash
git switch -C feature/new-feature
# ... make changes ...
git add .
git commit -m "Add: new feature"
git push -u origin feature/new-feature
```

### Syncing with Remote
```bash
git fetch origin
git merge origin/main
# or
git pull origin main
```

### Fixing Last Commit
```bash
# Edit your files
git add .
git commit --amend -m "New commit message"
git push --force
```

---

**Happy Git-ing!** 🚀
