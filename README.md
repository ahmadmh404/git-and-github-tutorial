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

## Pull Requests

after you made all chnages and the feature is ready to add
to the app or the codebase you need to merge it back to the
main branch, and it let's you share your code and changes
with your team for review and feedback once approved your
changes will become a part of the main branch keeping
the codebse stable and orgaize.

in your repo page press on the **Pull Requests** tab and press create new pull request.

then chose the branch **A** you want to merge and the branch **B** you want to merge the barnch **A** with
like i want to merge the changes in branch move-faster
to the branch main after a finished and tested my certain feature

then add a descroption if you want then press **Create Pull Request** and the senior dev will erview it later

## Understanding Git Conflicts

Git conflicts are often misunderstood. Here's a clear explanation of when conflicts do and don't occur.

### What Does NOT Cause Conflicts

- Having the same file in different branches
- Different changes to different parts of the same file
- Adding new files with the same name but different content
- Deleting a file in one branch while modifying it in another

### What DOES Cause Conflicts

- Changes to the exact same lines in different branches
- Overlapping changes in the same section of a file
- Both branches modifying the same section in different ways

### Conflict Examples

#### Example 1: No Conflict (Changes in Different Sections)

| Line | Branch A     | Branch B     |
| ---- | ------------ | ------------ |
| 1    | Hello        | Hello        |
| 2    | Changed in A | World        |
| 3    | World        | Changed in B |

✅ This merges automatically because changes are in different locations.

#### Example 2: Conflict (Changes in Same Section)

| Line | Branch A     | Branch B     |
| ---- | ------------ | ------------ |
| 1    | Hello        | Hello        |
| 2    | Changed to A | Changed to B |
| 3    | World        | World        |

⚠️ This causes a conflict because both branches changed Line 2.

### How Conflicts Appear in Git

When a conflict occurs, Git marks the file with conflict markers:

```text
Different changes in Branch B
```

### Resolving Conflicts

1. Identify conflicting sections (marked with `<<<<<<<`, `=======`, and `>>>>>>>`)
2. Choose which changes to keep:
   - Keep Branch A changes
   - Keep Branch B changes
   - Combine both changes
   - Write completely new code
3. Remove conflict markers
4. Save the file
5. Stage and commit the resolved changes

### Best Practices to Avoid Conflicts

| Practice            | Description                                        |
| ------------------- | -------------------------------------------------- |
| Frequent Pulls      | Keep your local branch updated with remote changes |
| Small Commits       | Make focused, single-purpose commits               |
| Clear Communication | Coordinate with team about who's working on what   |
| Branch Strategy     | Create feature branches from updated main branch   |
| Regular Merges      | Don't let branches diverge for too long            |

### Remember

- Conflicts are normal in collaborative development
- Git automatically merges what it can
- Only overlapping changes require manual resolution
- Good communication reduces conflict frequency

## What then?

- After approving your pull request by senior devs the
  merge happes in the remote repo, so to get those changes to your
  local repo you need to pull those changes with:

```bash
 # pull the changes
 git pull
```

- You can also do the merge via git CLI with thsi command:

```bash
git merge <branch-name>
```

- **Note**: the previous `git pull` command is short for the command below but git by default pulls from teh same branch you are on in the origin `remote`

```bash
git pull origin main
```

## Resolve the conflict issues steps:

- **First**: checkout to the man branch with this command:

```bash
git checkout main
```

- **Second**: pull the changes form the main branch which means the last merge before your merge `your team-mate code` with:

```bash
git pull
```

- Now your local main branch and original main branch are identical.

- **Third**: checkout to your own branch and to idetify the problem we will merge the main branch into our branch by this command:

```bash
git merge main
```

- now git will tell you you have a merge conflict and the merge fails

- Click `ctrl + 0` or whatever to open the merge conflict detector your code editor

- It will tell you about the merge conflicts and give you three choices

- Either to keep your code or your friend's code or merge both.

- when you choose the merge option you will chose either your or his code in the conflict
  lines

- AFter choosing the prefered lines from your codes click merge and the conflict is gone.

this is coming from `al branch`

Yo!, i am here!
