# Masterclass - Git for Beginners

## A Comprehensive Guide to Version Control

**Instructor**: Ishmeet Sethi
**Duration:** 60 minutes + Q&A
**Prerequisites:** Basic command line familiarity

---

## Table of Contents

1. [Introduction - Why Git Matters](#introduction)
2. [Understanding Version Control](#module-1-understanding-version-control)
3. [Git Core Concepts](#module-2-git-core-concepts)
4. [Setup and Configuration](#module-3-setup-and-configuration)
5. [Your First Repository](#module-4-your-first-repository)
6. [Essential Daily Workflow](#module-5-essential-daily-workflow)
7. [Branching Fundamentals](#module-6-branching-fundamentals)
8. [Essential Commands Reference](#module-7-essential-commands-reference)
9. [Common Scenarios & Troubleshooting](#module-8-common-scenarios--troubleshooting)
10. [Resources for Continued Learning](#resources)

---

## Introduction

### Why Git Matters

Before Git, developers faced common nightmares:

- Files named `project_final.txt`, `project_final_v2.txt`, `project_final_ACTUAL_FINAL.txt`
- Files shared over email (Yes! I have seen that myself)
- Lost work due to accidental deletions or overwrites
- Difficulty collaborating
- No way to go back in time to see what broke your code

**Git solves all of these problems.**

### What You'll Learn Today

By the end of this masterclass, you will:

- ✅ Understand what Git is and why it's essential
- ✅ Know the difference between Git and platforms like GitHub, Gitlab
- ✅ Be able to create and clone repositories
- ✅ Perform the essential daily Git workflow
- ✅ Use branches to work on features safely
- ✅ Have a reference guide for the most common Git commands

---

## Module 1: Understanding Version Control

### The Problem Git Solves

Think of version control like "Track Changes" in Microsoft Word, but infinitely more powerful and designed for code. It lets you:

- Save snapshots of your project at any point in time
- See what changed, when, and by whom
- Experiment without fear of breaking things
- Collaborate with others seamlessly
- Go back in time if something goes wrong

### What is Git?

**Git is a distributed version control system (DVCS).**

Key characteristics:

- **Distributed:** Everyone has the complete history on their machine, not just on a central server
- **Fast:** Most operations are local, no network needed
- **Powerful:** Branching and merging are core features, not afterthoughts
- **Free and Open Source:** Created by Linus Torvalds in 2005

### Git vs. GitHub/GitLab/Bitbucket

This is a crucial distinction that confuses many beginners:


| Git                                 | GitHub/GitLab/Bitbucket                   |
| ------------------------------------- | ------------------------------------------- |
| The version control tool (software) | Hosting platforms for Git repositories    |
| Runs on your local machine          | Runs in the cloud (remote servers)        |
| Command-line tool                   | Web-based interface + additional features |
| Works completely offline            | Requires internet connection              |
| Free and open source                | Free tier + paid plans                    |

**You can use Git without ever using GitHub**, but GitHub adds:

- Cloud backup of your code
- Collaboration tools (pull requests, code reviews)
- Project management features
- Social coding (following developers, starring projects)
- CI/CD integrations

---

## Module 2: Git Core Concepts

### The Three States of Git

Understanding these three areas is fundamental to mastering Git:

```
Working Directory  →  Staging Area  →  Repository
```

1. **Working Directory:** Your project folder where you make changes to files
2. **Staging Area (Index):** A holding area where you prepare changes before committing
3. **Repository (.git directory):** Where Git permanently stores committed snapshots

**Workflow:**

```
Edit files → Add to staging → Commit to repository
```

### What is a Commit?

A **commit** is a snapshot of your project at a specific point in time.

Each commit contains:

- A unique identifier (SHA-1 hash): `a3f2b9c...`
- Your changes (what files were modified, added, or deleted)
- A commit message describing the changes
- Author information (name and email)
- Timestamp
- A pointer to the previous commit (parent)

### What is a Repository?

A **repository (repo)** is a folder that Git is tracking.

It contains:

- Your project files
- A hidden `.git` folder with all version history
- Configuration files

**Two types of repositories:**

1. **Local Repository:** On your computer
2. **Remote Repository:** On a server (like GitHub)

---

## Module 3: Setup and Configuration

**Duration:** 10 minutes

### Installing Git

**Check if Git is already installed:**

```bash
git --version
```

**Installation:**

- **macOS:** Install Xcode Command Line Tools or download from [git-scm.com](https://git-scm.com)
- **Windows:** Download from [git-scm.com](https://git-scm.com) or use Git Bash
- **Linux:** `sudo apt-get install git` (Ubuntu/Debian) or `sudo yum install git` (Fedora)

### First-Time Configuration

**Set your identity** (required for every commit):

```bash
git config --global user.name "Your Name"
git config --global user.email "your.email@example.com"
```

**Set default branch name to 'main'** (optional, modern convention):

```bash
git config --global init.defaultBranch main
```

**View your configuration:**

```bash
git config --list
```

**View specific setting:**

```bash
git config user.name
```

### Creating a GitHub Account

1. Go to [github.com](https://github.com)
2. Sign up with your email
3. Verify your email address
4. Choose a username (this will be public)

**That's it!** We'll connect Git to GitHub later.

---

## Module 4: Your First Repository

### Option 1: Creating a New Local Repository

**Step 1:** Create a project folder and navigate into it

```bash
mkdir my-first-project
cd my-first-project
```

**Step 2:** Initialize Git

```bash
git init
```

What just happened?

- Git created a hidden `.git` folder in your project
- This folder contains all the version control magic
- Your folder is now a Git repository!

**Step 3:** Create your first file

```bash
echo "# My First Project" > README.md
```

**Step 4:** Check the status

```bash
git status
```

You'll see:

```
On branch main
No commits yet
Untracked files:
  README.md
```

**Step 5:** Stage the file

```bash
git add README.md
```

Or stage all files:

```bash
git add .
```

**Step 6:** Commit the file

```bash
git commit -m "Initial commit"
```

**Step 7:** View your commit history

```bash
git log
```

You'll see your commit with:

- Commit hash
- Author
- Date
- Commit message

**Shorter log view:**

```bash
git log --oneline
```

### Option 2: Cloning an Existing Repository

**What is cloning?**
Cloning downloads a complete copy of a repository from a remote server to your local machine, including all history.

**Clone a repository:**

```bash
git clone https://github.com/username/repository-name.git
```

**Clone into a specific folder:**

```bash
git clone https://github.com/username/repository-name.git my-folder-name
```

**What you get:**

- All project files
- Complete commit history
- All branches
- Connection to the remote repository (called "origin")

**Navigate into the cloned repository:**

```bash
cd repository-name
```

**Check the remote connection:**

```bash
git remote -v
```

---

## Module 5: Essential Daily Workflow

### The Standard Git Workflow

This is what you'll do every single day as a developer:

```
1. Pull latest changes    →  git pull
2. Make your changes      →  (edit files)
3. Check what changed     →  git status
4. Stage your changes     →  git add
5. Commit your changes    →  git commit
6. Push to remote         →  git push
```

### Step-by-Step Workflow

#### 1. Pull Latest Changes

**Switch to the default branch, and pull latest changes before you start working:**

```bash
git pull
```

This fetches and merges changes from the remote repository. It prevents merge conflicts later.

If the repository is up to date, you'll see:

```
Already up to date.
```

#### 2. Make Your Changes

Edit files in your text editor or IDE. Add new files, modify existing ones, delete files – whatever your project needs.

#### 3. Check What Changed

**See the status of your working directory:**

```bash
git status
```

This shows:

- Untracked files (new files Git doesn't know about)
- Modified files (tracked files you've changed)
- Staged files (files ready to be committed)

**See detailed differences:**

```bash
git diff
```

This shows line-by-line what changed in your files.

**See differences for staged files:**

```bash
git diff --staged
```

#### 4. Stage Your Changes

**Stage a specific file:**

```bash
git add filename.txt
```

**Stage multiple files:**

```bash
git add file1.txt file2.txt
```

**Stage all changed files:**

```bash
git add .
```

**Stage all files of a certain type:**

```bash
git add *.js
```

**💡 Tip:** The staging area lets you commit related changes together, even if you've edited many files.

#### 5. Commit Your Changes

**Commit with a message:**

```bash
git commit -m "Add user authentication feature"
```

**Best practices for commit messages:**

- ✅ Use present tense: "Add feature" not "Added feature"
- ✅ Be descriptive but concise
- ✅ Explain *what* and *why*, not *how*
- ✅ Start with a capital letter
- ❌ Avoid vague messages like "fixed stuff" or "updates"

**Examples of good commit messages:**

```bash
git commit -m "Fix login button alignment on mobile"
git commit -m "Add password validation to signup form"
git commit -m "Update README with installation instructions"
git commit -m "Remove deprecated API endpoints"
```

**Commit with a detailed message (opens editor):**

```bash
git commit
```

This opens your configured editor for a longer message with a title and description.

**Skip staging and commit all tracked files:**

```bash
git commit -am "Quick fix for typo"
```

⚠️ This only works for modified files, not new files.

#### 6. Push to Remote Repository

**Push your commits to GitHub/GitLab:**

```bash
git push
```

If this is your first push on a new branch, you may need:

```bash
git push -u origin main
```

The `-u` flag sets the upstream branch, so future pushes can just be `git push`.

### Working with Remote Repositories

**View your remote repositories:**

```bash
git remote -v
```

**Add a remote repository:**

```bash
git remote add origin https://github.com/username/repo-name.git
```

**Change the remote URL:**

```bash
git remote set-url origin https://github.com/username/new-repo.git
```

**Remove a remote:**

```bash
git remote remove origin
```

### Fetching vs. Pulling

**Fetch** downloads changes but doesn't merge them:

```bash
git fetch
```

**Pull** fetches and merges changes:

```bash
git pull
```

**Pull is essentially:**

```bash
git fetch + git merge
```

---

## Module 6: Branching Fundamentals

### Why Branches?

Branches let you work on features, experiments, or bug fixes **without affecting the main codebase**.

**Use cases:**

- Developing a new feature
- Fixing a bug
- Experimenting with an idea
- Working on different versions (production, staging, development)

**The golden rule:** The `main` (or `master` or `develop`) branch should always be stable and deployable.

### Understanding Branches

**Think of branches as parallel universes:**

- Each branch is an independent line of development
- Changes in one branch don't affect other branches
- You can switch between branches instantly
- Eventually, you merge branches back together

**Default branch:** When you create a repo, you start on the `main` branch.

### Branch Commands

#### View Branches

**List all local branches:**

```bash
git branch
```

The current branch is marked with `*`:

```
* main
  feature-login
  bugfix-header
```

**List all branches including remote:**

```bash
git branch -a
```

#### Create a New Branch

**Create a new branch:**

```bash
git branch feature-name
```

This creates the branch but doesn't switch to it.

**Create and switch to a new branch:**

```bash
git checkout -b feature-name
```

💡 **Naming conventions:**

- `feature/` prefix for new features: `feature/user-authentication`
- `bugfix/` prefix for bug fixes: `bugfix/login-error`
- `hotfix/` prefix for urgent fixes: `hotfix/security-patch`
- `your-name/` prefix if working in large teams: `ishmeet/feature/oauth`
- Use hyphens, not spaces or underscores

#### Switch Between Branches

**Switch to an existing branch:**

```bash
git checkout branch-name
```

**Switch back to main:**

```bash
git checkout main
```

⚠️ **Before switching branches:**

- Commit your changes, or
- Stash your changes (covered later)

Otherwise, you'll get an error or lose your work.

#### Make Changes on a Branch

**Example workflow:**

```bash
# Create and switch to a new branch
git checkout -b feature/add-footer

# Make changes to files

# Stage and commit
git add index.html
git commit -m "Add footer to homepage"

# Push the branch to remote
git push -u origin feature/add-footer
```

#### Merge Branches

**Merging** combines changes from one branch into another.

**Example: Merge a feature branch into main:**

```bash
# 1. Switch to the branch you want to merge INTO (usually main)
git checkout main

# 2. Make sure main is up to date
git pull

# 3. Merge the feature branch
git merge feature/add-footer

# 4. Push the updated main branch
git push
```

**What happens:**

- Git combines the changes from both branches
- If there are no conflicts, it creates a merge commit
- The feature branch still exists but can be deleted

#### Delete a Branch

**Delete a local branch** (after merging):

```bash
git branch -d feature-name
```

**Force delete** (if not merged):

```bash
git branch -D feature-name
```

**Delete a remote branch:**

```bash
git push origin --delete feature-name
```

### Branch Workflow Example

```bash
# Start on main branch
git checkout main
git pull

# Create a new feature branch
git checkout -b feature/user-profile

# Make changes and commit
echo "User profile page" > profile.html
git add profile.html
git commit -m "Create user profile page"

# Push the branch
git push -u origin feature/user-profile

# Switch back to main
git checkout main

# Notice profile.html doesn't exist here!
ls

# Merge the feature when ready
git merge feature/user-profile

# Delete the feature branch
git branch -d feature/user-profile
git push origin --delete feature/user-profile
```

---

## Module 7: Essential Commands Reference

### The 10 Commands That Cover 90% of Daily Git Usage


| Command        | Purpose                           | Example                                      |
| ---------------- | ----------------------------------- | ---------------------------------------------- |
| `git status`   | Check current state of repository | `git status`                                 |
| `git add`      | Stage files for commit            | `git add .`                                  |
| `git commit`   | Save changes with a message       | `git commit -m "Add feature"`                |
| `git push`     | Upload commits to remote          | `git push`                                   |
| `git pull`     | Download and merge remote changes | `git pull`                                   |
| `git clone`    | Copy a repository                 | `git clone https://github.com/user/repo.git` |
| `git branch`   | List, create, or delete branches  | `git branch feature-x`                       |
| `git checkout` | Switch branches or restore files  | `git checkout main`                          |
| `git merge`    | Combine branches                  | `git merge feature-x`                        |
| `git log`      | View commit history               | `git log --oneline`                          |

### Quick Command Reference

#### Configuration

```bash
git config --global user.name "Name"        # Set your name
git config --global user.email "email"      # Set your email
git config --list                           # View all settings
```

#### Repository Setup

```bash
git init                                    # Initialize a new repo
git clone <url>                             # Clone a remote repo
```

#### Basic Workflow

```bash
git status                                  # Check status
git add <file>                              # Stage a file
git add .                                   # Stage all changes
git commit -m "message"                     # Commit with message
git push                                    # Push to remote
git pull                                    # Pull from remote
```

#### Branching

```bash
git branch                                  # List branches
git branch <name>                           # Create branch
git checkout <name>                         # Switch branch
git checkout -b <name>                      # Create and switch
git merge <branch>                          # Merge branch
git branch -d <name>                        # Delete branch
```

#### Viewing History

```bash
git log                                     # Full commit history
git log --oneline                           # Condensed history
git log --graph                             # Visual branch graph
git diff                                    # See unstaged changes
git diff --staged                           # See staged changes
```

#### Remote Repositories

```bash
git remote -v                               # List remotes
git remote add origin <url>                 # Add remote
git push -u origin main                     # Push and set upstream
git fetch                                   # Fetch remote changes
```

---

## Module 8: Common Scenarios & Troubleshooting

### Undoing Changes

#### Unstage a File

**Problem:** You staged a file but don't want to commit it yet.

```bash
git reset HEAD <filename>
```

#### Discard Changes in Working Directory

**Problem:** You made changes to a file but want to revert to the last committed version.

```bash
git checkout -- <filename>
```

⚠️ **Warning:** This permanently deletes your uncommitted changes!

#### Undo the Last Commit (Keep Changes)

**Problem:** You committed too early and want to modify the commit.

```bash
git reset --soft HEAD~1
```

This undoes the commit but keeps your changes staged.

#### Undo the Last Commit (Discard Changes)

**Problem:** You made a commit you want to completely remove.

```bash
git reset --hard HEAD~1
```

⚠️ **Warning:** This permanently deletes your changes!

#### Amend the Last Commit

**Problem:** You made a typo in the commit message or forgot to add a file.

```bash
# Fix your files, then:
git add <forgotten-file>
git commit --amend -m "New commit message"
```

This replaces the last commit with a new one.

⚠️ **Never amend commits that have been pushed to remote!**

### Stashing Changes

**Use case:** You're working on something but need to switch branches quickly without committing.

**Save your work temporarily:**

```bash
git stash
```

Or with a message:

```bash
git stash save "Work in progress on login feature"
```

**View your stashes:**

```bash
git stash list
```

**Apply the most recent stash:**

```bash
git stash apply
```

Or apply a specific stash:

```bash
git stash apply stash@{0}
```

**Apply and remove the stash:**

```bash
git stash pop
```

**Delete a stash:**

```bash
git stash drop stash@{0}
```

**Clear all stashes:**

```bash
git stash clear
```

### Resolving Merge Conflicts

**What is a merge conflict?**
When Git can't automatically merge changes because the same lines were modified in different branches.

**Example scenario:**

```bash
git merge feature-branch
# Output: CONFLICT (content): Merge conflict in index.html
```

**How to resolve:**

1. **Open the conflicted file.** You'll see markers like:

```html
<<<<<<< HEAD
<h1>Welcome to Our Site</h1>
=======
<h1>Welcome to My Website</h1>
>>>>>>> feature-branch
```

2. **Edit the file to keep the desired changes:**

```html
<h1>Welcome to Our Website</h1>
```

3. **Remove the conflict markers** (`<<<<<<<`, `=======`, `>>>>>>>`)
4. **Stage the resolved file:**

```bash
git add index.html
```

5. **Complete the merge:**

```bash
git commit -m "Resolve merge conflict in index.html"
```

**Abort a merge:**

```bash
git merge --abort
```

### Other Common Issues

#### Check Out a Remote Branch

**Problem:** A colleague created a branch and you want to work on it.

```bash
git fetch
git checkout remote-feature-branch
```

Git automatically tracks the remote branch.

#### See What Changed in a Commit

```bash
git show <commit-hash>
```

Or for the last commit:

```bash
git show HEAD
```

#### Rename a Branch

```bash
git branch -m old-name new-name
```

Or rename the current branch:

```bash
git branch -m new-name
```

#### Ignore Files

Create a `.gitignore` file in your repository root:

```bash
# .gitignore example
node_modules/
.env
*.log
.DS_Store
dist/
```

Git will ignore these files and folders.

**Common .gitignore patterns:**

- `*.log` - Ignore all log files
- `folder/` - Ignore entire folder
- `!important.log` - Don't ignore this file (exception)

---

## Resources for Continued Learning

### Official Documentation

- [Git Official Documentation](https://git-scm.com/doc)
- [GitHub Guides](https://guides.github.com/)
- [GitLab Git Handbook](https://about.gitlab.com/handbook/git-page-update/)

### Interactive Tutorials

- [Learn Git Branching](https://learngitbranching.js.org/) - Visual, interactive tutorial
- [GitHub Skills](https://skills.github.com/) - Hands-on courses
- [Codecademy Git Course](https://www.codecademy.com/learn/learn-git)

### Books

- *Pro Git* by Scott Chacon (Free online)
- *Git Pocket Guide* by Richard E. Silverman

### Cheat Sheets

- [GitHub Git Cheat Sheet](https://education.github.com/git-cheat-sheet-education.pdf)
- [Atlassian Git Cheat Sheet](https://www.atlassian.com/git/tutorials/atlassian-git-cheatsheet)

### Advanced Topics

- Git hooks (automation)
- Rebasing (alternative to merging)
- Cherry-picking commits
- Bisecting (finding bugs)
- Submodules (repositories within repositories)
- Git workflows (GitFlow, GitHub Flow, etc.)

---

## Quick Reference Card

### First-Time Setup

```bash
git config --global user.name "Your Name"
git config --global user.email "your.email@example.com"
git config --global init.defaultBranch main
```

### Daily Workflow

```bash
git pull                              # Start your day
# ... make changes ...
git status                            # See what changed
git add .                             # Stage all changes
git commit -m "Descriptive message"   # Commit
git push                              # Push to remote
```

### Branching Workflow

```bash
git checkout -b feature/new-feature   # Create and switch to branch
# ... make changes and commit ...
git push -u origin feature/new-feature  # Push branch
git checkout main                     # Switch back to main
git pull                              # Update main
git merge feature/new-feature         # Merge feature
git push                              # Push merged changes
git branch -d feature/new-feature     # Delete local branch
```

### Emergency Commands

```bash
git stash                             # Save work in progress
git stash pop                         # Restore stashed work
git reset HEAD <file>                 # Unstage file
git checkout -- <file>                # Discard changes
git reset --soft HEAD~1               # Undo last commit, keep changes
```

---

## Key Takeaways

✅ **Git is a distributed version control system** that tracks changes in your code  
✅ **GitHub/GitLab are platforms** that host Git repositories in the cloud  
✅ **Commits are snapshots** of your project at specific points in time  
✅ **Branches let you work safely** without breaking the main codebase  
✅ **The daily workflow** is: pull → change → add → commit → push  
✅ **10 commands cover 90% of usage:** status, add, commit, push, pull, clone, branch, checkout, merge, log  
✅ **Git is forgiving** - most mistakes can be undone  
✅ **Practice is key** - use Git for every project, even personal ones  

---

## Next Steps

1. **Create a GitHub account** if you haven't already
2. **Initialize Git in your next project** from day one
3. **Commit often** - small, focused commits are better than large ones
4. **Use branches** for every feature or bug fix
5. **Read error messages** - Git is usually telling you exactly what's wrong
6. **Don't be afraid to experiment** - you can always reset or revert
7. **Explore GitHub** - star projects, follow developers, read code

---

**Prepared by:** Ishmeet Sethi  
**Date:** 12/17/2025  
**Contact:** sethi.ishmeet@gmail.com | [LinkedIn](https://www.linkedin.com/in/ishmeetsinghsethi)

---

**License:** This guide is free to use and share for educational purposes.
**Feedback:** If you have suggestions or found errors, you can reach out to me at sethi.ishmeet@gmail.com
