# Git Interview Questions (Intermediate)

Source PDF: `Git Interview Questions.pdf`

Curated from source questions with technical corrections and interview-focused wording.

## Question Index

- [1. What is a git repository?](#q-1)
- [2. How will you create a git repository?](#q-2)
- [3. Can you tell the difference between Git and GitHub?](#q-3)
- [4. What is a detached HEAD and what causes this and how to avoid this?](#q-4)
- [5. What is the difference between git stash apply vs git stash pop command?](#q-5)
- [6. How to revert a bad commit which is already pushed?](#q-6)
<a id="q-1"></a>
## 1. Question
What is a git repository?

### Answer
A Git repository is a versioned data store containing commits, trees, blobs, refs, and configuration. It tracks complete change history so teams can branch, review, merge, and recover work safely.

### Code Snippet
```bash
# Inspect repository history
git log --oneline --graph --decorate
```

### Keywords/Tags
- git
- intermediate

### Difficulty
- intermediate

### Related Questions
- Add cross-links to related topic files as content grows.

[Back to Question Index](#question-index)

<a id="q-2"></a>
## 2. Question
How will you create a git repository?

### Answer
Create a repository using `git init` for a new local project or `git clone` for an existing remote. After initialization, add files, commit history, and optionally configure a remote for collaboration.

### Code Snippet
```bash
# Initialize new repository
git init

# Track current files and create first commit
git add .
git commit -m "Initial commit"
```

### Keywords/Tags
- git
- intermediate

### Difficulty
- intermediate

### Related Questions
- Add cross-links to related topic files as content grows.

[Back to Question Index](#question-index)

<a id="q-3"></a>
## 3. Question
Can you tell the difference between Git and GitHub?

### Answer
Git is the distributed version control system; GitHub is a hosting/collaboration platform built around Git repositories. Git handles commits/branches locally, while GitHub adds PRs, issues, permissions, and CI integrations.

### Code Snippet
```bash
# Git (local operations)
git log --oneline

# GitHub (remote integration via git remote)
git remote add origin https://github.com/org/repo.git
```

### Keywords/Tags
- git
- intermediate

### Difficulty
- intermediate

### Related Questions
- Add cross-links to related topic files as content grows.

[Back to Question Index](#question-index)

<a id="q-4"></a>
## 4. Question
What is a detached HEAD and what causes this and how to avoid this?

### Answer
Detached HEAD means `HEAD` points directly to a commit instead of a branch reference, usually after checking out a commit/tag. Commits made there can be lost unless you create a branch from that state.

### Code Snippet
```bash
# Checkout a commit causes detached HEAD
git checkout a1b2c3d

# Recover by creating a branch from current state
git switch -c fix/detached-head-work
```

### Keywords/Tags
- git
- intermediate

### Difficulty
- intermediate

### Related Questions
- Add cross-links to related topic files as content grows.

[Back to Question Index](#question-index)

<a id="q-5"></a>
## 5. Question
What is the difference between git stash apply vs git stash pop command?

### Answer
`git stash apply` reapplies stashed changes but keeps the stash entry. `git stash pop` reapplies and removes the stash entry if successful. `apply` is safer when you may need to retry.

### Code Snippet
```bash
# Keep stash entry after applying
git stash apply stash@{0}

# Apply and remove stash entry
git stash pop
```

### Keywords/Tags
- git
- intermediate

### Difficulty
- intermediate

### Related Questions
- Add cross-links to related topic files as content grows.

[Back to Question Index](#question-index)

<a id="q-6"></a>
## 6. Question
How to revert a bad commit which is already pushed?

### Answer
Use `git revert <commit>` to create a new commit that undoes the bad change while preserving shared history. Avoid force-pushing rewritten history on shared branches unless explicitly coordinated.

### Code Snippet
```bash
# Safe undo for shared branch history
git revert <bad_commit_sha>

# Push revert commit to remote branch
git push origin main
```

### Keywords/Tags
- git
- intermediate

### Difficulty
- intermediate

### Related Questions
- Add cross-links to related topic files as content grows.

[Back to Question Index](#question-index)

