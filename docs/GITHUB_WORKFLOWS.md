# 🐙 GitHub Workflows Guide

Learn how to collaborate effectively using GitHub!

---

## 📑 Table of Contents

1. [Getting Started](#getting-started)
2. [Forking Workflow](#forking-workflow)
3. [Pull Request Process](#pull-request-process)
4. [Code Review](#code-review)
5. [GitHub Features](#github-features)

---

## 🚀 Getting Started

### Create a GitHub Account

Visit [github.com](https://github.com) and sign up for a free account.

### Set Up SSH Keys (Recommended)

```bash
# Generate SSH key
ssh-keygen -t ed25519 -C "your_email@example.com"

# Start SSH agent
eval "$(ssh-agent -s)"

# Add key to agent
ssh-add ~/.ssh/id_ed25519

# Copy public key
cat ~/.ssh/id_ed25519.pub | pbcopy

# Add to GitHub: Settings → SSH and GPG keys → New SSH key
```

---

## 🍴 Forking Workflow

### Step 1: Fork the Repository

1. Navigate to the repository on GitHub
2. Click the **Fork** button in the top-right
3. Select your account

### Step 2: Clone Your Fork

```bash
git clone https://github.com/YOUR_USERNAME/REPO_NAME.git
cd REPO_NAME
```

### Step 3: Add Upstream Remote

```bash
git remote add upstream https://github.com/ORIGINAL_OWNER/REPO_NAME.git
git remote -v
```

### Step 4: Keep Your Fork Updated

```bash
git fetch upstream
git switch main
git merge upstream/main
git push origin main
```

---

## 📬 Pull Request Process

### Creating a Pull Request

1. **Create a branch** from main:
   ```bash
   git switch -C feature/your-feature
   ```

2. **Make your changes** and commit:
   ```bash
   git add .
   git commit -m "Add: your feature description"
   ```

3. **Push to GitHub**:
   ```bash
   git push -u origin feature/your-feature
   ```

4. **Open a Pull Request**:
   - Go to your fork on GitHub
   - Click "Compare & pull request"
   - Fill in the PR template
   - Submit!

### PR Best Practices

✅ **Do:**
- Use descriptive titles
- Link related issues (`Fixes #123`)
- Keep PRs small and focused
- Write clear descriptions
- Add screenshots for UI changes

❌ **Don't:**
- Submit huge PRs (1000+ lines)
- Mix unrelated changes
- Forget to test your changes
- Ignore CI failures

---

## 👀 Code Review

### For Reviewers

- Be constructive and kind
- Explain *why* something should change
- Suggest alternatives when possible
- Acknowledge good work

### For Authors

- Respond to all feedback
- Make requested changes promptly
- Ask questions if unsure
- Thank your reviewers

---

## ✨ GitHub Features

### Issues

Use issues to track bugs, enhancements, and questions.

**Good Issue Template:**
```markdown
### Description
Brief description of the issue

### Steps to Reproduce
1. Step one
2. Step two
3. Step three

### Expected Behavior
What should happen

### Actual Behavior
What actually happens

### Environment
- OS: 
- Browser: 
- Version: 
```

### Projects

GitHub Projects helps you organize work with Kanban boards.

**Common Columns:**
- 📋 Backlog
- 🔄 In Progress
- 👀 In Review
- ✅ Done

### Discussions

Use Discussions for:
- 💡 Ideas
- ❓ Q&A
- 📢 Announcements
- 💬 General conversations

### Actions

Automate your workflow with GitHub Actions.

**Example: CI Pipeline**
```yaml
name: CI
on: [push, pull_request]
jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - name: Run tests
        run: npm test
```

### Releases

Create releases to distribute your project.

1. Go to **Releases** → **Draft a new release**
2. Choose a tag (e.g., `v1.0.0`)
3. Write release notes
4. Publish!

---

## 🏷️ GitHub Flow

A simple workflow for continuous deployment:

```
1. Create a branch
2. Make changes
3. Open a PR
4. Review and discuss
5. Deploy and test
6. Merge to main
```

---

## 📊 GitHub Insights

### Pulse

See recent activity in your repository.

### Traffic

View clones, views, and referrers.

### Contributors

See who's contributing to your project.

### Community

Check your community health metrics.

---

## 🎯 Pro Tips

1. **Use @mentions** to notify people
2. **Use #references** to link issues and PRs
3. **Use reactions** 👍 👎 🎉 to give quick feedback
4. **Pin important issues** and PRs
5. **Use labels** to categorize issues
6. **Set up CODEOWNERS** for automatic reviews

---

## 📚 Resources

- [GitHub Docs](https://docs.github.com)
- [GitHub Learning Lab](https://lab.github.com)
- [Pro Git Book](https://git-scm.com/book)

---

**Happy Collaborating!** 🤝
