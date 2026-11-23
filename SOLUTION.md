# Git Selective Commit Management – Complete Practical Solution

This documentation explains how to complete the Git branching and selective commit task from the beginning.

It is written for beginners who have never worked with Git or GitHub before.

By following this guide, you will learn how to create a GitHub repository, work with commits, create branches, and selectively transfer commits using Git.

---

# Table of Contents

1. Introduction to Git and GitHub
2. Understanding Important Git Concepts
3. Prerequisites and Installation
4. Create a GitHub Repository
5. Clone the Repository
6. Configure Git Identity
7. Create the Initial Project Commit
8. Simulate Developer A's Commit
9. Simulate Developer B's Commit
10. Simulate Developer C's Commit
11. Verify All Commits
12. Create a New Branch
13. Cherry-Pick Developer A's Commit
14. Cherry-Pick Developer B's Commit
15. Verify the New Branch
16. Push the New Branch to GitHub
17. Compare Both Branches
18. Final Verification
19. Important Git Commands Reference
20. Conclusion

---

# 1. Introduction to Git and GitHub

Before starting the practical implementation, let's understand Git and GitHub.

## What is Git?

Git is a free and open-source version control system.

It helps developers track changes in their code, save different versions of a project, and work with multiple developers.

For example, if you make changes to a project today and want to check what the project looked like yesterday, Git helps you track those changes.

## What is GitHub?

GitHub is an online platform that allows developers to store Git repositories and collaborate with other developers.

Git manages your project's version history locally, while GitHub hosts your repository online.

## Difference Between Git and GitHub

| Git | GitHub |
|---|---|
| Version control system | Online code hosting platform |
| Works on your computer | Accessible through the internet |
| Tracks code changes | Stores and shares repositories |
| Manages branches and commits | Displays branches and commits online |
| Developed as an open-source project | A Microsoft-owned platform |

---

# 2. Understanding Important Git Concepts

Before executing commands, understand these basic terms.

### 2.1 Repository

A repository is a location where your project's files and version history are stored.

Example:

`git-demo-branch`

### 2.2 Commit

A commit is a saved snapshot of your project at a particular point in time.

Every commit has:
- A unique commit ID (hash).
- An author name.
- An author email.
- A commit message.
- The changes included in that commit.

Example:

`Add user authentication feature`

### 2.3 Branch

A branch is a separate line of development.

It allows developers to work on different features without directly changing another branch.

Example:

- `main`
- `developer-a-b`
- `feature-login`

### 2.4 Main Branch

The `main` branch is generally the primary branch of a repository.

In this practical, all three developers initially commit their work to `main`.

### 2.5 Cherry-Pick

`git cherry-pick` is a Git command that applies a specific existing commit to your current branch.

For example:

Suppose the main branch contains:

- Commit A
- Commit B
- Commit C

You only want A and B.

Instead of merging the entire main branch, you can cherry-pick A and B individually.

This is the main concept used to complete this assignment.

### 2.6 Remote

A remote is a reference to a repository hosted somewhere else, usually GitHub.

In this project, `origin` is the name of our GitHub remote.

---

# 3. Prerequisites and Installation

Before starting, make sure you have the following:

1. A GitHub account.
2. Git installed on your computer.
3. Visual Studio Code installed.
4. An internet connection.

## Install Git

Download Git from:

https://git-scm.com/downloads

Follow the installation instructions for Windows.

## Install Visual Studio Code

Download VS Code from:

https://code.visualstudio.com/

## Verify Git Installation

Open PowerShell or the VS Code terminal.

Run:

```bash
git --version
```

Expected output (the version number may differ):

```text
git version 2.x.x
```

If you see a Git version, Git is installed successfully.

---

# 4. Create a GitHub Repository

A GitHub repository is where we will store our project online.

### Step 1: Open GitHub

Visit:

https://github.com/

Sign in to your GitHub account.

### Step 2: Create a repository

1. Click the `+` icon in the top-right corner.
2. Select `New repository`.
3. Enter the following details:

| Setting | Value |
|---|---|
| Repository Name | git-demo-branch |
| Description | Git branching and selective commit demonstration |
| Visibility | Public |
| Add README | Unchecked |
| Add .gitignore | None |

4. Click `Create repository`.

### Why choose Public?

A public repository allows other people to view your project without requiring special access.

### Why not create a README initially?

We will create our own README file locally and push it to GitHub.

---

# 5. Clone the Repository

## What is cloning?

Cloning means downloading a repository from GitHub to your local computer.

This creates a local copy where you can edit files, create commits, and work with branches.

### Step 1: Copy the repository URL

Open your newly created GitHub repository.

1. Click the green `Code` button.
2. Select HTTPS.
3. Copy the repository URL.

Example:

```text
https://github.com/YOUR-USERNAME/git-demo-branch.git
```

### Step 2: Open PowerShell

Navigate to the folder where you want to store your project.

Example:

```powershell
cd Desktop
```

### Step 3: Clone the repository

Run:

```bash
git clone https://github.com/YOUR-USERNAME/git-demo-branch.git
```

Replace `YOUR-USERNAME` with your GitHub username.

### Step 4: Enter the project folder

```bash
cd git-demo-branch
```

### Step 5: Open the project in VS Code

```bash
code .
```

### Step 6: Check repository status

```bash
git status
```

The repository is now available locally.

### What does git clone do?

It downloads the repository, its available branches, and its Git history to your computer.

---

# 6. Configure Git Identity

Git stores the author's name and email address with each commit.

For this assignment, we will simulate three developers using different Git identities.

We will use the `git -c` option to provide a different identity for each commit.

For the initial commit, use your own name and GitHub-associated email.

Example:

```bash
git -c user.name="Project Admin" -c user.email="YOUR-EMAIL" commit -m "Initial project setup"
```

For the simulated developers, we will use:

| Person | Name | Example Email |
|---|---|---|
| Project Admin | Project Admin | Your GitHub email |
| Developer A | Developer A | developer-a@example.com |
| Developer B | Developer B | developer-b@example.com |
| Developer C | Developer C | developer-c@example.com |

**Important:** These developer identities are simulated for this practical. They do not represent actual GitHub accounts or collaborators.

You can also configure your normal Git identity permanently using:

```bash
git config --global user.name "Your Name"
git config --global user.email "YOUR-EMAIL"
```

Check your configuration:

```bash
git config --global --list
```

---

# 7. Create the Initial Project Commit

The initial commit creates the starting point of our project.

### Step 1: Create README.md

Inside VS Code:

1. Open Explorer.
2. Click New File.
3. Enter `README.md`.
4. Add the following content:

```markdown
# Git Demo Branch

This project demonstrates Git branching
and selective commits using cherry-pick.
```

5. Save the file.

### Step 2: Stage the file

```bash
git add README.md
```

**Why use git add?**

Git has a staging area. The `git add` command places selected changes into that area so they can be included in the next commit.

### Step 3: Create the initial commit

```bash
git -c user.name="Project Admin" -c user.email="YOUR-EMAIL" commit -m "Initial project setup"
```

**Why use git commit?**

It saves the staged changes as a new commit in the local repository.

### Step 4: Push the commit to GitHub

```bash
git push -u origin main
```

**Why use git push?**

It uploads local commits to the remote GitHub repository.

The `-u` option sets the upstream tracking branch, making future pushes easier.

Our initial project is now available on GitHub.

---

# 8. Simulate Developer A's Commit

Now we will simulate Developer A working on user authentication.

### Step 1: Create a file

Create a new file:

`developer-a.txt`

Add:

```text
Developer A
Feature: User Authentication
Status: Completed
```

Save the file.

### Step 2: Stage the file

```bash
git add developer-a.txt
```

This adds the new file to the staging area.

### Step 3: Commit Developer A's changes

```bash
git -c user.name="Developer A" -c user.email="developer-a@example.com" commit -m "Add user authentication feature"
```

This creates a commit with Developer A's identity.

### Step 4: Push to GitHub

```bash
git push origin main
```

Developer A's changes are now available on the remote `main` branch.

---

# 9. Simulate Developer B's Commit

Developer B is working on dashboard management.

### Step 1: Create a file

Create:

`developer-b.txt`

Add:

```text
Developer B
Feature: Dashboard Management
Status: Completed
```

Save the file.

### Step 2: Stage the file

```bash
git add developer-b.txt
```

### Step 3: Commit Developer B's changes

```bash
git -c user.name="Developer B" -c user.email="developer-b@example.com" commit -m "Add dashboard management feature"
```

### Step 4: Push to GitHub

```bash
git push origin main
```

Developer B's changes are now available on `main`.

---

# 10. Simulate Developer C's Commit

Developer C is working on payment integration.

### Step 1: Create a file

Create:

`developer-c.txt`

Add:

```text
Developer C
Feature: Payment Integration
Status: Completed
```

Save the file.

### Step 2: Stage the file

```bash
git add developer-c.txt
```

### Step 3: Commit Developer C's changes

```bash
git -c user.name="Developer C" -c user.email="developer-c@example.com" commit -m "Add payment integration feature"
```

### Step 4: Push to GitHub

```bash
git push origin main
```

Now all three developers have committed their work to `main`.

---

# 11. Verify All Commits

Before creating the new branch, we need to check whether all commits are present.

Run:

```bash
git log --oneline --graph --decorate
```

### Understanding this command

- `git log`: Displays commit history.
- `--oneline`: Displays each commit in a single line.
- `--graph`: Displays the commit history graphically.
- `--decorate`: Displays branch and tag references.

### Expected output

Your commit IDs will be different if you repeat this exercise.

Example:

```text
24949e0 Add payment integration feature
1fe804d Add dashboard management feature
6065188 Add user authentication feature
771f6a9 Initial project setup
```

Record the commit hashes of:

- Initial commit: `771f6a9`
- Developer A: `6065188`
- Developer B: `1fe804d`
- Developer C: `24949e0`

These are example hashes from this practical. Use your own actual hashes when following the instructions.

---

# 12. Create a New Branch

Now comes the most important part.

We want a new branch that starts from the initial commit, rather than the latest `main` commit.

Why?

Because the latest `main` commit already contains Developer C's changes.

### Step 1: Understand the command

```bash
git switch -c developer-a-b 771f6a9
```

### Explanation

| Part | Meaning |
|---|---|
| git switch | Switch to another branch |
| -c | Create a new branch |
| developer-a-b | New branch name |
| 771f6a9 | Starting commit (initial commit) |

This creates the new branch from the initial commit and switches to it.

**Important:** The `main` branch remains unchanged.

### Step 2: Verify the branch

```bash
git branch
```

Expected output:

```text
* developer-a-b
  main
```

The asterisk `*` identifies your currently active branch.

---

# 13. Cherry-Pick Developer A's Commit

We are now on the `developer-a-b` branch.

We want to bring Developer A's user authentication commit into this branch.

### Step 1: Run cherry-pick

```bash
git cherry-pick 6065188
```

Replace the hash with your actual Developer A commit hash.

### Why use cherry-pick?

Because we want to transfer only one selected commit instead of merging the entire `main` branch.

Git creates a new commit on the current branch containing the selected changes.

### Step 2: Verify

```bash
git log --oneline
```

Expected:

```text
<new-hash> Add user authentication feature
771f6a9 Initial project setup
```

Developer A's changes are now included.

---

# 14. Cherry-Pick Developer B's Commit

Next, we want to include Developer B's dashboard feature.

### Step 1: Run cherry-pick

```bash
git cherry-pick 1fe804d
```

Replace the hash with your actual Developer B commit hash.

### Why use this command?

It applies Developer B's selected commit to the current branch without including Developer C's commit.

### Step 2: Verify

```bash
git log --oneline --graph --decorate
```

Expected output:

```text
<new-hash> Add dashboard management feature
<new-hash> Add user authentication feature
771f6a9 Initial project setup
```

Our new branch now contains the initial commit and the selected work of Developers A and B.

Developer C's commit has not been cherry-picked.

---

# 15. Verify the New Branch

Now we need to verify which files exist in the new branch.

Run:

```bash
git status
```

Then:

```bash
git log --oneline
```

You should see three commits:

1. Initial project setup
2. Add user authentication feature
3. Add dashboard management feature

Check the files in VS Code Explorer.

Expected files:

```text
git-demo-branch/
│
├── README.md
├── developer-a.txt
└── developer-b.txt
```

The file `developer-c.txt` should not exist in this branch.

This confirms that Developer C's file and commit were not included.

---

# 16. Push the New Branch to GitHub

Until now, the new branch exists locally.

To make it available on GitHub, we need to push it.

### Step 1: Check the active branch

```bash
git branch
```

Make sure the active branch is:

```text
* developer-a-b
  main
```

### Step 2: Push the branch

```bash
git push -u origin developer-a-b
```

### Why use this command?

- `git push`: Uploads commits to GitHub.
- `origin`: Refers to the remote repository.
- `developer-a-b`: Specifies the branch to upload.
- `-u`: Sets the upstream tracking branch.

Your new branch is now available on GitHub.

---

# 17. Compare Both Branches

This step proves that our task was completed correctly.

We will compare the original `main` branch with the new `developer-a-b` branch.

### Step 1: Display main branch commits

```bash
git log main --oneline
```

Expected:

```text
24949e0 Add payment integration feature
1fe804d Add dashboard management feature
6065188 Add user authentication feature
771f6a9 Initial project setup
```

### Step 2: Display new branch commits

```bash
git log developer-a-b --oneline
```

Expected:

```text
<new-hash> Add dashboard management feature
<new-hash> Add user authentication feature
771f6a9 Initial project setup
```

### Step 3: Identify excluded commits

Run:

```bash
git log developer-a-b..main --oneline
```

### What does this command mean?

It displays commits reachable from `main` that are not reachable from `developer-a-b`.

Expected output:

```text
24949e0 Add payment integration feature
```

This confirms that Developer C's commit was excluded.

---

# 18. Final Verification

We have successfully completed the task.

Let's compare the results.

| Requirement | Main | developer-a-b |
|---|---|---|
| Initial project setup | Yes | Yes |
| Developer A commit | Yes | Yes |
| Developer B commit | Yes | Yes |
| Developer C commit | Yes | No |

### Expected GitHub Repository Structure

On the `main` branch:

```text
git-demo-branch/
│
├── README.md
├── developer-a.txt
├── developer-b.txt
└── developer-c.txt
```

On the `developer-a-b` branch:

```text
git-demo-branch/
│
├── README.md
├── developer-a.txt
└── developer-b.txt
```

The two branches are available in the same public GitHub repository.

**Important:** The original `main` branch was not modified or deleted. Only selected commits were applied to the new branch.

---

# 19. Important Git Commands Reference

Here are all the important commands used in this practical.

| Command | Purpose |
|---|---|
| `git --version` | Check Git installation |
| `git clone URL` | Download a GitHub repository |
| `git status` | Check current changes |
| `git add filename` | Stage a file |
| `git commit -m "message"` | Save staged changes |
| `git push origin main` | Push commits to main |
| `git branch` | List local branches |
| `git switch branch-name` | Switch branches |
| `git switch -c branch-name HASH` | Create a branch from a commit |
| `git cherry-pick HASH` | Apply a selected commit |
| `git log --oneline` | View commit history |
| `git log --graph --decorate` | View graphical commit history |
| `git push -u origin branch-name` | Publish a new branch |
| `git remote -v` | View remote repository URLs |
| `git config --global --list` | View Git configuration |

---

# 20. What If Something Goes Wrong?

### Problem 1: Git says permission denied (403)

This generally means the authenticated GitHub account does not have permission to push to the repository.

Solutions:
- Check which GitHub account is authenticated.
- Verify that the account has repository access.
- Authenticate with the correct account.
- Alternatively, configure SSH authentication.

### Problem 2: Cherry-pick causes a conflict

Sometimes two commits modify the same lines in a file.

Git may stop and ask you to resolve the conflict.

Check:

```bash
git status
```

Open the conflicting file in VS Code and resolve the conflict.

After fixing it:

```bash
git add .
git cherry-pick --continue
```

To cancel the cherry-pick instead:

```bash
git cherry-pick --abort
```

### Problem 3: Wrong branch is selected

Check:

```bash
git branch
```

Switch to the required branch:

```bash
git switch developer-a-b
```

### Problem 4: Developer C's commit is accidentally included

If you have already completed a cherry-pick and want to undo that commit, first check that your working tree is clean.

If it is the latest commit on your new branch:

```bash
git reset --hard HEAD~1
```

**Warning:** This command discards the latest commit and any uncommitted changes. Use it only after confirming that the latest commit is the unwanted one.

---

# 21. Conclusion

In this practical, we learned how Git and GitHub help developers manage source code and collaborate on projects.

We created a public GitHub repository, simulated three developers, and pushed their commits to the same `main` branch.

After that, we created a new branch named `developer-a-b` from the initial commit.

Using `git cherry-pick`, we selectively applied Developer A's and Developer B's commits while excluding Developer C's commit.

Finally, we pushed the new branch to GitHub and verified the results using Git commit history and branch comparison commands.

### Final Learning Outcomes

After completing this practical, you should understand:

- The difference between Git and GitHub.
- How to create and manage GitHub repositories.
- How to clone repositories.
- How to stage, commit, and push changes.
- How to create and switch branches.
- How to identify commits using commit hashes.
- How to use `git cherry-pick`.
- How to exclude unwanted commits.
- How to compare branches and verify commit history.

**The most important learning from this assignment is that `git cherry-pick` allows developers to transfer specific commits between branches without merging all the changes from the source branch.**

---

**End of Documentation**