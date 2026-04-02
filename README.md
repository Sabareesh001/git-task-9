# Task 9: Working with Remote Repositories and Collaboration

## Objective

Learn how to work with remote repositories and collaborate with others:

- Set up a local repository and connect it to a remote
- Create and push feature branches
- Simulate a Pull Request workflow
- Merge changes and pull updates from remote
- Understand collaboration best practices

## Setup Instructions

This task is part of the git-fundamentals project. Ensure you have:

- Git installed on your system
- A GitHub account (or GitLab/other Git hosting service)
- Access to create repositories on your Git hosting service
- A code editor (VS Code recommended)
- Familiarity with branching and basic Git commands

## Exercise Overview

This task simulates a real-world collaborative workflow where multiple developers work on the same project using remote repositories.

### 1. Setting Up a Remote Repository

**Step 1: Create a remote repository**

Go to GitHub/GitLab and create a new empty repository. Note the URL:

```
https://github.com/username/repo-name.git
```

**Step 2: Initialize local repository**

```bash
# In your task-9 directory
git init
git add .
git commit -m "Initial commit"
```

**Step 3: Connect to remote**

```bash
# Add the remote repository
git remote add origin https://github.com/username/repo-name.git

# Verify the remote is added
git remote -v
```

**Step 4: Push to remote**

```bash
# Push the main branch to remote
git branch -M main
git push -u origin main
```

### 2. Creating a Feature Branch

**Workflow:**

```bash
# Create and switch to a new feature branch
git checkout -b feature/add-content

# Make changes to files
# Edit index.html or create new files
```

**Example commit:**

```bash
git add .
git commit -m "feat: Add welcome section to homepage"
```

### 3. Pushing Feature Branch to Remote

```bash
# Push the feature branch to remote
git push -u origin feature/add-content

# Verify it's on remote
git branch -r
```

### 4. Pull Request / Merge Request Workflow

**On GitHub:**

1. Go to the repository
2. Click "Compare & pull request" button
3. Add a title and description:
   - Title: "Add welcome section to homepage"
   - Description: "This PR adds a welcome message to the homepage"
4. Click "Create Pull Request"

**Review Process:**

- Check for code quality
- Leave comments if needed
- Approve or request changes

### 5. Merging the PR

**After approval:**

1. Click "Merge pull request" on GitHub
2. Choose merge strategy (default: Create a merge commit)
3. Click "Confirm merge"
4. Delete the remote branch (optional but recommended)

### 6. Updating Local Repository

**After merging on remote:**

```bash
# Switch to main branch
git checkout main

# Fetch latest changes from remote
git fetch origin

# Pull the merged changes
git pull origin main

# Clean up: delete local feature branch
git branch -d feature/add-content
```

### 7. Git Commands Reference

**Branch Management:**

```bash
# Create a new branch
git checkout -b feature/name

# List local branches
git branch

# List remote branches
git branch -r

# Delete local branch
git branch -d feature/name

# Delete remote branch
git push origin --delete feature/name
```

**Remote Operations:**

```bash
# Check remote configuration
git remote -v

# Add a remote
git remote add origin <url>

# Push to remote
git push origin main
git push -u origin feature/name

# Pull from remote
git pull origin main

# Fetch without merging
git fetch origin
```

**Collaboration:**

```bash
# See who made each change
git log --oneline

# See changes in a commit
git show <commit-hash>

# See changes before committing
git diff
```

### 8. Best Practices for Remote Collaboration

1. **Always pull before push** - Get latest changes before pushing
   ```bash
   git pull origin main
   git push origin main
   ```

2. **Use descriptive branch names** - Make it clear what the branch does
   ```bash
   feature/add-login
   feature/fix-bug-123
   docs/update-readme
   ```

3. **Write clear commit messages** - Help others understand your changes
   ```bash
   git commit -m "feat: Add user authentication"
   git commit -m "fix: Resolve memory leak in parser"
   ```

4. **Small, focused commits** - Easier to review and understand
   ```bash
   # Good: One feature per commit
   git commit -m "Add login form styling"
   git commit -m "Add login validation logic"
   
   # Avoid: Multiple unrelated changes in one commit
   ```

5. **Keep branches up to date** - Reduce merge conflicts
   ```bash
   git fetch origin
   git merge origin/main
   ```

6. **Delete merged branches** - Keep repository clean
   ```bash
   git push origin --delete feature/name
   git branch -d feature/name
   ```

### 9. Handling Merge Conflicts from Remote

If conflicts occur during `git pull`:

```bash
# Resolve conflicts in your editor
# Then stage and commit
git add .
git commit -m "Resolve merge conflicts"
git push origin main
```

### 10. Workflow Summary

```
1. Create branch locally
   └─ git checkout -b feature/name

2. Make changes and commit
   └─ git commit -m "description"

3. Push to remote
   └─ git push -u origin feature/name

4. Create Pull Request on GitHub
   └─ Review and approve

5. Merge on GitHub
   └─ Delete remote branch

6. Update local repository
   └─ git checkout main
   └─ git pull origin main
   └─ git branch -d feature/name
```

This workflow is commonly used in professional development teams!
