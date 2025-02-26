# Git Complete Guide

## Setting Up Git and Connecting to GitHub

### Configure Git with Your Identity
```sh
git config --global user.name "Your Name"
git config --global user.email "your-email@example.com"
```

### Initialize a Git Repository
```sh
git init
```

### Connect to a Remote Repository
```sh
git remote add origin https://github.com/your-username/your-repo.git
```

### List Remote Repository
```sh
git remote -v
```

### Clone an Existing Repository
```sh
git clone https://github.com/your-username/your-repo.git
```

### Check the Status of Your Repository
```sh
git status
```

### Staging and Committing Changes
```sh
git add .  # Stages all changes
git commit -m "Your commit message"
```

### Push Changes to GitHub
```sh
git push origin main  # Pushes to the main branch
```

### Pull Latest Changes from GitHub
```sh
git pull origin main
```

### Creating and Switching Branches
```sh
git branch new-branch  # Create a new branch
git checkout new-branch  # Switch to the new branch
git checkout -b new-branch  # Create and switch to a new branch
```

### Merging Branches
```sh
git checkout main  # Switch to main branch
git merge new-branch  # Merge new-branch into main
```

### Deleting a Branch
```sh
git branch -d new-branch  # Delete a branch locally
git push origin --delete new-branch  # Delete a branch remotely
```

### Resolving Merge Conflicts
1. Open conflicting files.
2. Edit and resolve conflicts manually.
3. Stage resolved files: `git add .`
4. Commit the merge: `git commit -m "Resolved merge conflicts"`

### Undoing Changes
```sh
git reset HEAD~1  # Undo last commit but keep changes
git reset --hard HEAD~1  # Undo last commit and discard changes
git revert <commit-hash>  # Revert a specific commit
```

### Viewing Commit History
```sh
git log  # View full commit history
git log --oneline  # View compact commit history
```

### Checking Remote Branches
```sh
git branch -r  # List all remote branches
```

### Fetching Remote Changes
```sh
git fetch origin  # Fetch latest changes without merging
```

### Stashing Changes
```sh
git stash  # Save uncommitted changes
git stash pop  # Apply stashed changes
git stash list  # View stash list
```

### Git Tags
```sh
git tag v1.0  # Create a tag
git push origin v1.0  # Push tag to GitHub
git tag -d v1.0  # Delete a tag locally
git push origin --delete v1.0  # Delete tag remotely
```

This guide covers essential Git commands for managing repositories and working efficiently with GitHub.

