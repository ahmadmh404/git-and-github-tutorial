# Git Commands Reference

## Basic Concepts

- **Repo**: The folder that holds all versions of your projects
- **Branch**: A parallel folder of your project

## Initial Setup

```bash
# Configure your identity
git config --global user.name 'your name'
git config --global user.email 'your email'

# Initialize repository
git init
```

## Basic Commands

### Checking Status

```bash
git status
```

Shows the status of your repo and new/modified files in your current folder that are different from the repo.

### Staging Changes

```bash
# Stage specific file
git add <filename>
```

Makes a snapshot of a project at a certain point (like a version) to be able to return to it if something goes wrong in the future.

```bash
# Stage all changes
git add .
```

The dot (.) will add all files (new, modified, or deleted) to git tracking.

### Committing Changes

```bash
git commit
```

This will commit the changes you staged in the previous step.

### Viewing History

```bash
git log
```

View all commits made.

### Branch Management

```bash
# Rename branch
git branch -m <old> <new>

# Time travel to specific commit
git checkout <commit_id>
```

When using checkout to a specific commit, your files in later commits are preserved - you're just shifting between points in time.

```bash
# Return to latest state
git checkout main

# Force return to main
git checkout -f main
```

Use force (-f) in case of any mistakes in the detached state that you want to discard.

## Repository Types

### Local Repository

- Created when using `git init` in your folder

### Remote Repository

- When you upload your repo to a server like:
  - GitHub
  - GitLab
  - Bitbucket
- Used to share code with co-workers
- Keeps project versions in sync across different users' computers

### Remote Repository Structure

- Public repo on each device of users sharing the project
- Main repo on the server that users sync their public repos with

## Remote Operations

### Setting Up Remote

```bash
# Add remote repository
git remote add origin <link>
```

Note: When cloning from GitHub, it automatically names the repo "origin" (default name/alias for the remote URL)

### Pushing Changes

```bash
# Push to remote with upstream tracking
git push -u origin main
```

Pushes your local commits to GitHub (same as --set-upstream)

## Branch Operations

### Creating and Managing Branches

```bash
# Create new branch
git branch <branch-name>

# Switch to branch
git checkout <branch-name>

# Create and switch in one command
git checkout -b <branch-name>
```

When creating a new branch, it inherits code from your current branch, not always from main.

### Pro Tip

```bash
# Create branch from specific source
git branch <new-branch-name> <source-branch>
```

Use when you want to create a branch based on another branch while being on a different one.

### Publishing Branches

```bash
# Set upstream for feature branch
git push --set-upstream origin <branch-name>
# or
git push -u origin <feature-branch>
```

Links your local feature branch with a remote feature branch for tracking.

### Synchronizing

```bash
# Pull changes
git pull
```

Syncs your local branch with the remote (server) branch.
