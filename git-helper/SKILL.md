---
name: git-helper
description: Execute Git commands and manage Git repositories. Use when the user wants to perform Git operations like checking status, creating commits, switching branches, viewing logs, or performing remote operations (push, pull, fetch). Triggers include mentions of 'git', repository operations, commits, branches, GitHub integration, or version control tasks.
---

# Git Helper

## Overview

This skill helps execute Git commands and manage Git repositories efficiently. It handles common Git workflows including status checks, commits, branch management, history viewing, and remote operations with GitHub.

## Common Operations

### Check Repository Status

When the user asks about git status or repository state:

```bash
git status
```

Show a clear summary of:
- Current branch
- Staged changes
- Unstaged changes
- Untracked files

### View Commit History

When the user asks for commit history or recent commits:

```bash
# Last N commits
git log -n 5 --oneline --decorate

# Detailed view with changes
git log -n 5 --stat

# With graph visualization
git log -n 10 --oneline --graph --all --decorate
```

### Create Commits

When the user wants to create a new commit:

1. First, show current status with `git status`
2. Stage files if needed:
   ```bash
   git add <files>
   # or stage all changes
   git add -A
   ```
3. Create the commit:
   ```bash
   git commit -m "Commit message"
   ```

Always confirm what will be committed before executing.

### Branch Operations

**Switch branches:**
```bash
git checkout <branch-name>
# or with newer syntax
git switch <branch-name>
```

**Create new branch:**
```bash
git checkout -b <new-branch-name>
# or
git switch -c <new-branch-name>
```

**List branches:**
```bash
git branch -a  # all branches including remote
git branch     # local branches only
```

**Delete branch:**
```bash
git branch -d <branch-name>  # safe delete
git branch -D <branch-name>  # force delete
```

### View Differences

**See unstaged changes:**
```bash
git diff
```

**See staged changes:**
```bash
git diff --staged
```

**Compare branches:**
```bash
git diff <branch1>..<branch2>
```

### Remote Operations

**Fetch updates:**
```bash
git fetch origin
```

**Pull changes:**
```bash
git pull origin <branch-name>
# or for current branch
git pull
```

**Push changes:**
```bash
git push origin <branch-name>
# or for current branch
git push
```

**View remote info:**
```bash
git remote -v
git remote show origin
```

### Merge Operations

**Merge a branch:**
```bash
git merge <branch-name>
```

Always check for conflicts after merging and help resolve them if needed.

### Stash Operations

**Save work temporarily:**
```bash
git stash save "description"
# or simply
git stash
```

**List stashes:**
```bash
git stash list
```

**Apply stashed changes:**
```bash
git stash apply
# or specific stash
git stash apply stash@{0}
```

**Pop (apply and remove):**
```bash
git stash pop
```

## GitHub Integration

### Clone Repository

```bash
git clone https://github.com/username/repository.git
# or with SSH
git clone git@github.com:username/repository.git
```

### Set Remote URL

```bash
git remote add origin https://github.com/username/repository.git
# or change existing
git remote set-url origin https://github.com/username/repository.git
```

### Pull Requests Workflow

1. Create feature branch
2. Make changes and commit
3. Push to GitHub: `git push -u origin <branch-name>`
4. Create PR via GitHub web interface (inform user about this step)

## Best Practices

### Before Executing Commands

1. Always run `git status` first to understand the current state
2. Confirm destructive operations with the user
3. Check if there are uncommitted changes before switching branches
4. Verify the current branch before pushing

### Commit Messages

Encourage clear, descriptive commit messages:
- Use present tense ("Add feature" not "Added feature")
- Keep first line under 50 characters
- Add detailed description if needed after blank line

### Safety Checks

Before force operations (push -f, reset --hard, etc.), always:
1. Warn the user about potential data loss
2. Suggest safer alternatives
3. Get explicit confirmation

### Error Handling

When Git commands fail:
1. Show the exact error message
2. Explain what went wrong in simple terms
3. Suggest corrective actions
4. Offer to execute the fix if appropriate

## Workflow Examples

### Example 1: Creating a commit
```
User: "Neuer commit 'Add login feature'"
Claude: 
1. Runs: git status
2. Shows current changes
3. Asks if user wants to stage all changes or specific files
4. Stages files: git add -A
5. Creates commit: git commit -m "Add login feature"
6. Confirms success
```

### Example 2: Switching branches
```
User: "Wechsle zu branch feature/authentication"
Claude:
1. Runs: git status (check for uncommitted changes)
2. If changes exist, asks user to commit or stash first
3. Switches: git checkout feature/authentication
4. Confirms the switch with current branch info
```

### Example 3: Viewing history
```
User: "Die letzten 5 commits?"
Claude:
Runs: git log -n 5 --oneline --decorate
Shows formatted output with commit hashes and messages
```

## Common Issues & Solutions

### Merge Conflicts
When conflicts occur:
1. Show conflicted files: `git status`
2. Explain the conflict markers (<<<<, ====, >>>>)
3. Help user resolve conflicts
4. Stage resolved files: `git add <files>`
5. Complete merge: `git commit`

### Detached HEAD State
If in detached HEAD:
1. Explain the situation
2. Suggest creating a branch: `git checkout -b <new-branch>`
3. Or return to a branch: `git checkout <branch-name>`

### Push Rejected
If push is rejected:
1. Pull first: `git pull origin <branch>`
2. Resolve any conflicts
3. Push again: `git push origin <branch>`

## Working Directory

Always execute Git commands in the repository's root directory. If user hasn't specified a repository location, ask for it or check the current working directory with `pwd`.
