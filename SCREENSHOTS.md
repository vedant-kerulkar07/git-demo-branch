# Git Practical – Command Execution Screenshots

This document contains screenshots of the commands executed during the Git branching and selective commit practical.

The screenshots provide visual proof of the implementation and help beginners understand the commands and their outputs.

## Table of Contents

1. Git Installation Verification
2. GitHub Repository Cloning
3. Initial Project Commit
4. Developer A Commit
5. Developer B Commit
6. Developer C Commit
7. Git Commit History
8. Creating a New Branch
9. Cherry-Picking Developer A's Commit
10. Cherry-Picking Developer B's Commit
11. Final Branch Verification
12. Pushing the New Branch to GitHub
13. Comparing Both Branches
14. GitHub Repository Final Result

---

## 1. Git Installation Verification

**Command:**

```bash
git --version
```

**Description:** Verifies that Git is installed successfully.

**Screenshot:**

![Git Version](screenshots/01-git-version.png)

---

## 2. GitHub Repository Cloning

**Command:**

```bash
git clone REPOSITORY_URL
```

**Description:** Downloads the public GitHub repository to the local computer.

**Screenshot:**

![Git Clone](screenshots/02-git-clone.png)

---

## 3. Initial Project Commit

**Commands:**

```bash
git add README.md

git commit -m "Initial project setup"

git push origin main
```

**Description:** Creates and pushes the initial project commit.

**Screenshot:**

![Initial Commit](screenshots/03-initial-commit.png)

---

## 4. Developer A Commit

**Commands:**

```bash
git add developer-a.txt

git commit -m "Add user authentication feature"

git push origin main
```

**Description:** Adds Developer A's user authentication feature to the main branch.

**Screenshot:**

![Developer A Commit](screenshots/04-developer-a.png)

---

## 5. Developer B Commit

**Commands:**

```bash
git add developer-b.txt

git commit -m "Add dashboard management feature"

git push origin main
```

**Description:** Adds Developer B's dashboard management feature to the main branch.

**Screenshot:**

![Developer B Commit](screenshots/05-developer-b.png)

---

## 6. Developer C Commit

**Commands:**

```bash
git add developer-c.txt

git commit -m "Add payment integration feature"

git push origin main
```

**Description:** Adds Developer C's payment integration feature to the main branch.

**Screenshot:**

![Developer C Commit](screenshots/06-developer-c.png)

---

## 7. Git Commit History

**Command:**

```bash
git log --oneline --graph --decorate
```

**Description:** Displays all commits in the main branch.

**Screenshot:**

![Git Commit History](screenshots/07-commit-history.png)

---

## 8. Creating a New Branch

**Command:**

```bash
git switch -c developer-a-b INITIAL_COMMIT_HASH
```

**Description:** Creates a new branch from the initial project commit.

**Screenshot:**

![New Branch](screenshots/08-create-branch.png)

---

## 9. Cherry-Picking Developer A's Commit

**Command:**

```bash
git cherry-pick DEVELOPER_A_COMMIT_HASH
```

**Description:** Applies only Developer A's commit to the new branch.

**Screenshot:**

![Developer A Cherry Pick](screenshots/09-cherry-pick-a.png)

---

## 10. Cherry-Picking Developer B's Commit

**Command:**

```bash
git cherry-pick DEVELOPER_B_COMMIT_HASH
```

**Description:** Applies only Developer B's commit to the new branch.

**Screenshot:**

![Developer B Cherry Pick](screenshots/10-cherry-pick-b.png)

---

## 11. Final Branch Verification

**Commands:**

```bash
git branch

git log --oneline --graph --decorate

git status
```

**Description:** Verifies that the new branch contains the initial commit and Developer A and B commits.

**Screenshot:**

![Final Branch Verification](screenshots/11-final-verification.png)

---

## 12. Pushing the New Branch to GitHub

**Command:**

```bash
git push -u origin developer-a-b
```

**Description:** Uploads the new branch to the public GitHub repository.

**Screenshot:**

![Push New Branch](screenshots/12-push-branch.png)

---

## 13. Comparing Both Branches

**Commands:**

```bash
git log main --oneline

git log developer-a-b --oneline

git log developer-a-b..main --oneline
```

**Description:** Compares both branches and identifies the commit that was excluded.

**Screenshot:**

![Branch Comparison](screenshots/13-branch-comparison.png)

---

## 14. GitHub Repository Final Result

**Description:** Shows the final public GitHub repository and its available branches.

**Screenshot:**

![GitHub Final Result](screenshots/14-github-final.png)

---

## Conclusion

The screenshots demonstrate the successful execution of the Git branching and selective commit management practical.

They provide visual evidence that:

- Three developers committed their changes to the main branch.
- A new branch was created from the initial commit.
- Developer A and Developer B commits were selectively applied.
- Developer C's commit was excluded.
- The new branch was successfully pushed to GitHub.

**End of Screenshot Documentation**