Below is a well-structured README-style Git cheat sheet that you can directly use in your projects or GitHub repositories. It includes most commonly used Git commands with explanations, grouped logically so it's easy to understand and remember.


---

📘 Git Complete Cheat Sheet (Beginner → Advanced)

A comprehensive guide to understanding and using Git version control system with detailed explanations and examples.


---

1️⃣ What is Git?

Git is a distributed version control system used to track changes in source code during software development.

Key Features

Tracks file changes

Allows collaboration with multiple developers

Supports branching and merging

Maintains complete history of the project

Enables rollback to previous versions



---

2️⃣ Installing Git

Linux

sudo apt install git

Mac

brew install git

Windows

Download from:

https://git-scm.com/

Check installation:

git --version


---

3️⃣ Initial Git Configuration

Set username and email globally.

git config --global user.name "Your Name"
git config --global user.email "your@email.com"

Check configuration:

git config --list


---

4️⃣ Creating a Repository

Initialize Git in a project

git init

This creates a hidden folder:

.git

which stores all version history.


---

5️⃣ Git Workflow (Core Concept)

The Git workflow consists of three stages.

Working Directory → Staging Area → Repository

Stage	Description

Working Directory	Files you edit
Staging Area	Files prepared for commit
Repository	Permanent history



---

6️⃣ Checking Repository Status

git status

Shows:

modified files

staged files

untracked files



---

7️⃣ Adding Files to Staging

Add a single file

git add file.txt

Add multiple files

git add file1.txt file2.txt

Add all files

git add .


---

8️⃣ Commit Changes

Save changes to Git history.

git commit -m "Initial commit"

Best practice commit message:

<type>: short description

example:
fix: resolve login bug
feat: add user authentication


---

9️⃣ View Commit History

git log

Compact version:

git log --oneline

Graph view:

git log --graph --oneline --all


---

🔟 Undo Changes

Undo unstaged changes

git checkout -- file.txt

Remove file from staging

git reset file.txt

Undo last commit

git reset --soft HEAD~1

Remove commit but keep changes:

git reset --mixed HEAD~1

Delete commit permanently:

git reset --hard HEAD~1


---

1️⃣1️⃣ Working with Branches

Branches allow parallel development.

Create branch

git branch feature-login

Switch branch

git checkout feature-login

Or

git switch feature-login

Create and switch branch

git checkout -b feature-login


---

1️⃣2️⃣ List Branches

git branch

Shows local branches.

Remote branches:

git branch -r

All branches:

git branch -a


---

1️⃣3️⃣ Merge Branches

Merge branch into current branch.

git merge feature-login

Example workflow:

main
 └── feature-login

After merge:

main


---

1️⃣4️⃣ Delete Branch

git branch -d feature-login

Force delete:

git branch -D feature-login


---

1️⃣5️⃣ Working with Remote Repositories

Connect to GitHub or remote server.

Add remote

git remote add origin https://github.com/user/repo.git

Check remote:

git remote -v


---

1️⃣6️⃣ Push Code to Remote

git push origin main

Push new branch:

git push origin feature-login


---

1️⃣7️⃣ Pull Updates

Download latest changes.

git pull origin main

Pull = fetch + merge.


---

1️⃣8️⃣ Fetch Updates

git fetch origin

This downloads changes but does not merge them.


---

1️⃣9️⃣ Clone Repository

Copy remote repository locally.

git clone https://github.com/user/repo.git


---

2️⃣0️⃣ Git Diff

View differences between files.

git diff

Compare staged changes:

git diff --staged

Compare commits:

git diff commit1 commit2


---

2️⃣1️⃣ Stashing Changes

Temporarily save uncommitted work.

git stash

List stash:

git stash list

Apply stash:

git stash apply

Delete stash:

git stash drop


---

2️⃣2️⃣ Git Tags

Used for releases.

Create tag:

git tag v1.0

Annotated tag:

git tag -a v1.0 -m "Version 1.0"

Push tags:

git push origin --tags


---

2️⃣3️⃣ Rebase (Advanced)

Rebase moves commits to a new base.

git rebase main

Interactive rebase:

git rebase -i HEAD~3

Useful for:

cleaning commit history

squashing commits



---

2️⃣4️⃣ Git Reset vs Revert

Reset

Changes commit history.

git reset --hard HEAD~1

Revert

Creates new commit that undoes changes.

git revert commit_id

Safer for shared repositories.


---

2️⃣5️⃣ Git Ignore

Ignore files from tracking.

Create .gitignore.

Example:

node_modules/
*.log
.env
dist/


---

2️⃣6️⃣ Viewing File History

git blame file.py

Shows who modified each line.


---

2️⃣7️⃣ Git Cherry Pick

Apply specific commit from another branch.

git cherry-pick commit_id


---

2️⃣8️⃣ Git Clean

Remove untracked files.

git clean -f

Remove directories:

git clean -fd


---

2️⃣9️⃣ Git Aliases

Create shortcuts.

Example:

git config --global alias.st status
git config --global alias.cm commit
git config --global alias.co checkout

Use:

git st
git cm
git co


---

3️⃣0️⃣ Typical Git Workflow

Example daily workflow.

git pull origin main
git checkout -b new-feature

# make changes

git add .
git commit -m "feat: add new feature"

git push origin new-feature

Create Pull Request on GitHub.


---

3️⃣1️⃣ Git Best Practices

✔ Commit frequently
✔ Write meaningful commit messages
✔ Use branches for features
✔ Pull before pushing
✔ Never commit secrets


---

3️⃣2️⃣ Useful Git Visualization Tools

Tool	Purpose

GitKraken	Git GUI
SourceTree	Git GUI
Netron	Model visualization
GitLens	VS Code Git extension



---

3️⃣3️⃣ Git Internal Architecture

Git stores data as:

Blob → File content
Tree → Directory
Commit → Snapshot

Everything is stored inside:

.git/


---

3️⃣4️⃣ Common Git Errors

Permission denied

ssh-add ~/.ssh/id_rsa

Merge conflict

Resolve manually and commit.


---

🎯 Conclusion

Git enables:

Version control

Team collaboration

Code history tracking

Safe experimentation with branches


Mastering Git is essential for software engineering, ML engineering, and DevOps workflows.


---

If you want, I can also create a 🔥 "Git for ML Engineers & Data Scientists" cheat sheet, covering things like:

Git for large datasets

Git LFS

DVC

Versioning models, experiments, and checkpoints


which will be very useful for your Computer Vision / Deep Learning work.
