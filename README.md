# Git Branching and Selective Commit Management

## Problem Statement

Consider a project where three developers are working on the same GitHub repository. All three developers have completed their work and pushed their commits to the `main` branch.

The development team now receives a requirement to create a separate branch that contains only the work completed by Developer A and Developer B.

Developer C's changes must not be included in the new branch.

### Scenario

A project has three developers:

| Developer | Contribution | Commit |
|---|---|---|
| Developer A | User Authentication | Add user authentication feature |
| Developer B | Dashboard Management | Add dashboard management feature |
| Developer C | Payment Integration | Add payment integration feature |

All three developers have committed their changes to the same `main` branch.

### Task Requirements

1. Create a new public repository on GitHub.
2. Add project files and create commits representing three different developers.
3. Push all commits to the `main` branch.
4. Create a new branch named `developer-a-b`.
5. Include Developer A's commit in the new branch.
6. Include Developer B's commit in the new branch.
7. Exclude Developer C's commit from the new branch.
8. Push the new branch to GitHub.
9. Verify that the new branch contains only the required commits.
10. Keep the original `main` branch unchanged.

### Expected Result

**Main Branch**

- Initial Project Setup
- Developer A – User Authentication
- Developer B – Dashboard Management
- Developer C – Payment Integration

**New Branch: `developer-a-b`**

- Initial Project Setup
- Developer A – User Authentication
- Developer B – Dashboard Management

Developer C's payment integration commit must not appear in the new branch.

### Objective

The objective of this practical task is to understand Git and GitHub, work with branches, manage commits, and learn how to selectively transfer commits between branches using the `git cherry-pick` command.

### Technologies and Tools

- Git
- GitHub
- Visual Studio Code
- Windows PowerShell / Git Bash
- Markdown

### Important Git Concept

Git's `cherry-pick` command allows developers to apply specific commits from another branch without merging the entire branch history.

This makes it possible to include selected changes while excluding unwanted commits.

### Detailed Implementation

For the complete beginner-friendly instructions, Git commands, explanations, and verification steps, refer to [SOLUTION.md](SOLUTION.md).