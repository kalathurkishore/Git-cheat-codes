Below is the **same Git cheat sheet but formatted in a much cleaner, human-readable structure** (not README style, not cluttered). It reads like **notes you can quickly scan during work**.

---

# 📘 Git Complete Cheat Sheet (Beginner → Advanced)

A clear guide to the **Git version control system**, including commonly used commands and workflows.

---

# 1. What is Git?

Git is a **distributed version control system** used to track changes in source code during software development.

### Key Features

* Tracks file changes over time
* Enables collaboration among multiple developers
* Supports **branching and merging**
* Maintains full project history
* Allows rollback to previous versions

---

# 2. Installing Git

### Linux

```bash
sudo apt install git
```

### Mac

```bash
brew install git
```

### Windows

Download from:
[https://git-scm.com/](https://git-scm.com/)

### Check Installation

```bash
git --version
```

---

# 3. Initial Git Configuration

Set your **username and email**.

```bash
git config --global user.name "Your Name"
git config --global user.email "your@email.com"
```

Check configuration:

```bash
git config --list
```

---

# 4. Creating a Repository

Initialize Git inside a project folder.

```bash
git init
```

This creates a hidden folder:

```
.git
```

This folder stores the **entire version history**.

---

# 5. Git Workflow (Core Concept)

Git has **three main stages**.

```
Working Directory → Staging Area → Repository
```

| Stage             | Description               |
| ----------------- | ------------------------- |
| Working Directory | Files you edit            |
| Staging Area      | Files prepared for commit |
| Repository        | Permanent Git history     |

---

# 6. Checking Repository Status

```bash
git status
```

This shows:

* modified files
* staged files
* untracked files

---

# 7. Adding Files to Staging

### Add a single file

```bash
git add file.txt
```

### Add multiple files

```bash
git add file1.txt file2.txt
```

### Add everything

```bash
git add .
```

---

# 8. Commit Changes

Save changes permanently to Git history.

```bash
git commit -m "Initial commit"
```

### Recommended Commit Message Format

```
type: short description
```

Examples:

```
fix: resolve login bug
feat: add user authentication
docs: update readme
```

---

# 9. View Commit History

### Full history

```bash
git log
```

### Compact history

```bash
git log --oneline
```

### Graph view

```bash
git log --graph --oneline --all
```

---

# 10. Undo Changes

### Undo unstaged changes

```bash
git checkout -- file.txt
```

### Remove file from staging

```bash
git reset file.txt
```

### Undo last commit (keep changes staged)

```bash
git reset --soft HEAD~1
```

### Undo last commit (keep changes but unstage)

```bash
git reset --mixed HEAD~1
```

### Delete commit permanently

```bash
git reset --hard HEAD~1
```

---

# 11. Working with Branches

Branches allow **parallel development**.

### Create branch

```bash
git branch feature-login
```

### Switch branch

```bash
git checkout feature-login
```

or

```bash
git switch feature-login
```

### Create and switch in one step

```bash
git checkout -b feature-login
```

---

# 12. List Branches

### Local branches

```bash
git branch
```

### Remote branches

```bash
git branch -r
```

### All branches

```bash
git branch -a
```

---

# 13. Merge Branches

Merge a branch into the **current branch**.

```bash
git merge feature-login
```

Example structure:

```
main
 └── feature-login
```

After merging:

```
main
```

---

# 14. Delete Branch

Delete a branch.

```bash
git branch -d feature-login
```

Force delete:

```bash
git branch -D feature-login
```

---

# 15. Working with Remote Repositories

Connect your project to GitHub.

```bash
git remote add origin https://github.com/user/repo.git
```

Check remote repositories:

```bash
git remote -v
```

---

# 16. Push Code to Remote

Push code to remote repository.

```bash
git push origin main
```

Push a new branch:

```bash
git push origin feature-login
```

---

# 17. Pull Updates

Download and merge remote changes.

```bash
git pull origin main
```

Pull is equivalent to:

```
fetch + merge
```

---

# 18. Fetch Updates

Download updates **without merging**.

```bash
git fetch origin
```

---

# 19. Clone Repository

Copy a remote repository to your system.

```bash
git clone https://github.com/user/repo.git
```

---

# 20. Git Diff

View differences between files.

### Unstaged changes

```bash
git diff
```

### Staged changes

```bash
git diff --staged
```

### Compare commits

```bash
git diff commit1 commit2
```

---

# 21. Stashing Changes

Temporarily save unfinished work.

### Save changes

```bash
git stash
```

### List stashes

```bash
git stash list
```

### Apply stash

```bash
git stash apply
```

### Delete stash

```bash
git stash drop
```

---

# 22. Git Tags

Tags are used for **version releases**.

### Create tag

```bash
git tag v1.0
```

### Annotated tag

```bash
git tag -a v1.0 -m "Version 1.0"
```

### Push tags

```bash
git push origin --tags
```

---

# 23. Rebase (Advanced)

Rebase moves commits to a new base.

```bash
git rebase main
```

Interactive rebase:

```bash
git rebase -i HEAD~3
```

Used for:

* cleaning commit history
* squashing commits

---

# 24. Git Reset vs Git Revert

### Reset

Changes commit history.

```bash
git reset --hard HEAD~1
```

### Revert

Creates a **new commit that undoes changes**.

```bash
git revert commit_id
```

Safer for **shared repositories**.

---

# 25. Git Ignore

Ignore files from Git tracking.

Create a file:

```
.gitignore
```

Example:

```
node_modules/
*.log
.env
dist/
```

---

# 26. Viewing File History

```bash
git blame file.py
```

Shows **who modified each line**.

---

# 27. Git Cherry Pick

Apply a specific commit from another branch.

```bash
git cherry-pick commit_id
```

---

# 28. Git Clean

Remove untracked files.

```bash
git clean -f
```

Remove directories:

```bash
git clean -fd
```

---

# 29. Git Aliases

Create shortcuts for commands.

Example:

```bash
git config --global alias.st status
git config --global alias.cm commit
git config --global alias.co checkout
```

Usage:

```
git st
git cm
git co
```

---

# 30. Typical Git Workflow

Example daily workflow.

```bash
git pull origin main

git checkout -b new-feature

# make changes

git add .

git commit -m "feat: add new feature"

git push origin new-feature
```

Then create a **Pull Request on GitHub**.

---

# 31. Git Best Practices

✔ Commit frequently
✔ Write meaningful commit messages
✔ Use branches for features
✔ Pull before pushing
✔ Never commit secrets

---

# 32. Useful Git Tools

| Tool       | Purpose                          |
| ---------- | -------------------------------- |
| GitKraken  | Git GUI                          |
| SourceTree | Git GUI                          |
| GitLens    | VS Code Git extension            |
| Netron     | Model architecture visualization |

---

# 33. Git Internal Architecture

Git stores data as objects:

```
Blob   → File content
Tree   → Directory structure
Commit → Snapshot of repository
```

Everything is stored inside:

```
.git/
```

---

# 34. Common Git Errors

### Permission denied

```bash
ssh-add ~/.ssh/id_rsa
```

### Merge conflict

Resolve conflicts manually, then:

```bash
git add .
git commit
```

---

# 🎯 Conclusion

Git helps with:

* Version control
* Team collaboration
* Code history tracking
* Safe experimentation using branches

Git is **essential for software engineers, ML engineers, and DevOps workflows**.

---

✅ If you want, I can also make a **very powerful cheat sheet specifically for your domain (AI / ML / Computer Vision)** covering:

* **Git for large datasets**
* **Git LFS**
* **DVC**
* **Versioning ML models**
* **Experiment tracking**
* **Handling checkpoints & weights**

This will be **extremely useful for your CV / Deep Learning projects.**
