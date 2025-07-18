# Git Cheat Sheet 🚀

A comprehensive reference guide for Git commands organized by category.

## Table of Contents
- [Repository Setup](#repository-setup)
- [Basic Commands](#basic-commands)
- [Branching & Merging](#branching--merging)
- [Remote Repositories](#remote-repositories)
- [Stashing](#stashing)
- [Viewing History](#viewing-history)
- [Undoing Changes](#undoing-changes)
- [Tagging](#tagging)
- [Configuration](#configuration)
- [Advanced Commands](#advanced-commands)

---

## Repository Setup

### Initialize a new repository
```bash
git init
```

### Clone an existing repository
```bash
git clone <repository-url>
git clone <repository-url> <directory-name>
```

### Clone with specific branch
```bash
git clone -b <branch-name> <repository-url>
```

---

## Basic Commands

### Check repository status
```bash
git status
git status -s  # Short format
```

### Add files to staging area
```bash
git add <file-name>
git add .                    # Add all files
git add *.js                 # Add all JavaScript files
git add -A                   # Add all files including deleted ones
git add -p                   # Interactive staging
```

### Commit changes
```bash
git commit -m "commit message"
git commit -am "message"     # Add and commit in one step
git commit --amend           # Modify last commit
git commit --amend -m "new message"  # Change last commit message
```

### View differences
```bash
git diff                     # Working directory vs staging
git diff --cached            # Staging vs last commit
git diff HEAD                # Working directory vs last commit
git diff <branch1> <branch2> # Compare branches
```

---

## Branching & Merging

### List branches
```bash
git branch                   # Local branches
git branch -r                # Remote branches
git branch -a                # All branches
```

### Create and switch branches
```bash
git branch <branch-name>     # Create branch
git checkout <branch-name>   # Switch to branch
git checkout -b <branch-name> # Create and switch
git switch <branch-name>     # Modern way to switch
git switch -c <branch-name>  # Create and switch (modern)
```

### Merge branches
```bash
git merge <branch-name>      # Merge branch into current
git merge --no-ff <branch>   # Force merge commit
git merge --squash <branch>  # Squash merge
```

### Delete branches
```bash
git branch -d <branch-name>  # Delete merged branch
git branch -D <branch-name>  # Force delete branch
git push origin --delete <branch-name>  # Delete remote branch
```

### Rebase
```bash
git rebase <branch-name>     # Rebase current branch
git rebase -i HEAD~3         # Interactive rebase last 3 commits
git rebase --continue        # Continue after resolving conflicts
git rebase --abort           # Cancel rebase
```

---

## Remote Repositories

### Add remote repository
```bash
git remote add origin <repository-url>
git remote add upstream <repository-url>
```

### View remotes
```bash
git remote -v
git remote show origin
```

### Fetch and pull
```bash
git fetch                    # Fetch all branches
git fetch origin             # Fetch from origin
git pull                     # Fetch and merge
git pull origin <branch>     # Pull specific branch
git pull --rebase            # Pull with rebase
```

### Push changes
```bash
git push                     # Push to default remote
git push origin <branch>     # Push to specific branch
git push -u origin <branch>  # Set upstream and push
git push --force             # Force push (dangerous!)
git push --force-with-lease  # Safer force push
```

### Track remote branches
```bash
git branch --set-upstream-to=origin/<branch> <local-branch>
git push -u origin <branch>  # Set upstream while pushing
```

---

## Stashing

### Basic stashing
```bash
git stash                    # Stash current changes
git stash save "message"     # Stash with message
git stash -u                 # Include untracked files
git stash -a                 # Include all files
```

### Manage stashes
```bash
git stash list               # List all stashes
git stash show               # Show latest stash
git stash show stash@{1}     # Show specific stash
git stash apply              # Apply latest stash
git stash apply stash@{1}    # Apply specific stash
git stash pop                # Apply and remove stash
git stash drop               # Remove latest stash
git stash clear              # Remove all stashes
```

---

## Viewing History

### View commit history
```bash
git log                      # Full log
git log --oneline            # Compact log
git log --graph              # Visual graph
git log --all --graph --oneline  # All branches graph
git log -p                   # Show patches
git log --stat               # Show file statistics
git log --author="name"      # Filter by author
git log --since="2 weeks ago" # Filter by date
git log --grep="pattern"     # Filter by commit message
```

### View specific commits
```bash
git show <commit-hash>       # Show commit details
git show HEAD~1              # Show previous commit
git show --name-only <commit> # Show only file names
```

### Blame and annotation
```bash
git blame <file>             # Show who changed each line
git annotate <file>          # Similar to blame
```

---

## Undoing Changes

### Unstage files
```bash
git reset HEAD <file>        # Unstage specific file
git reset HEAD               # Unstage all files
git restore --staged <file>  # Modern way to unstage
```

### Discard changes
```bash
git checkout -- <file>       # Discard changes in working directory
git restore <file>           # Modern way to discard changes
git clean -f                 # Remove untracked files
git clean -fd                # Remove untracked files and directories
```

### Reset commits
```bash
git reset --soft HEAD~1      # Undo commit, keep changes staged
git reset --mixed HEAD~1     # Undo commit, keep changes unstaged
git reset --hard HEAD~1      # Undo commit, discard changes
git reset --hard <commit>    # Reset to specific commit
```

### Revert commits
```bash
git revert <commit-hash>     # Create new commit that undoes changes
git revert HEAD              # Revert last commit
git revert --no-commit <commit> # Revert without committing
```

---

## Tagging

### Create tags
```bash
git tag <tag-name>           # Lightweight tag
git tag -a <tag-name> -m "message" # Annotated tag
git tag -a <tag-name> <commit-hash> # Tag specific commit
```

### List and show tags
```bash
git tag                      # List all tags
git tag -l "v1.*"            # List tags matching pattern
git show <tag-name>          # Show tag details
```

### Push and delete tags
```bash
git push origin <tag-name>   # Push specific tag
git push origin --tags       # Push all tags
git tag -d <tag-name>        # Delete local tag
git push origin --delete <tag-name> # Delete remote tag
```

---

## Configuration

### Global configuration
```bash
git config --global user.name "Your Name"
git config --global user.email "your.email@example.com"
git config --global init.defaultBranch main
git config --global core.editor "code --wait"
git config --global merge.tool vimdiff
```

### Local configuration
```bash
git config user.name "Your Name"
git config user.email "your.email@example.com"
```

### View configuration
```bash
git config --list            # Show all config
git config --global --list   # Show global config
git config user.name         # Show specific config
```

### Aliases
```bash
git config --global alias.co checkout
git config --global alias.br branch
git config --global alias.ci commit
git config --global alias.st status
git config --global alias.lg "log --oneline --graph --all"
git config --global alias.unstage "reset HEAD --"
```

---

## Advanced Commands

### Cherry-pick
```bash
git cherry-pick <commit-hash> # Apply specific commit
git cherry-pick -n <commit>   # Cherry-pick without committing
git cherry-pick --continue    # Continue after resolving conflicts
```

### Bisect (find bugs)
```bash
git bisect start             # Start bisect session
git bisect bad               # Mark current commit as bad
git bisect good <commit>     # Mark commit as good
git bisect reset             # End bisect session
```

### Reflog
```bash
git reflog                   # Show reference log
git reflog expire            # Clean up reflog
git reflog show <branch>     # Show reflog for branch
```

### Worktree
```bash
git worktree add <path> <branch> # Create new worktree
git worktree list            # List worktrees
git worktree remove <path>   # Remove worktree
```

### Submodules
```bash
git submodule add <url> <path> # Add submodule
git submodule init           # Initialize submodules
git submodule update         # Update submodules
git submodule update --init --recursive # Init and update recursively
```

### Archive
```bash
git archive --format=zip --output=project.zip HEAD # Create zip of current state
git archive --format=tar --output=project.tar HEAD # Create tar archive
```

---

## Useful Git Aliases

Add these to your `.gitconfig` file or use the config commands:

```bash
# Quick aliases
git config --global alias.co checkout
git config --global alias.br branch
git config --global alias.ci commit
git config --global alias.st status

# Advanced aliases
git config --global alias.unstage 'reset HEAD --'
git config --global alias.last 'log -1 HEAD'
git config --global alias.visual '!gitk'
git config --global alias.lg "log --color --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit"
git config --global alias.tree "log --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit --all"
```

---

## Common Workflows

### Feature Branch Workflow
```bash
# Create feature branch
git checkout -b feature/new-feature

# Work on feature, commit changes
git add .
git commit -m "Add new feature"

# Push feature branch
git push -u origin feature/new-feature

# Merge back to main (after PR/MR)
git checkout main
git pull origin main
git merge feature/new-feature
git push origin main

# Clean up
git branch -d feature/new-feature
git push origin --delete feature/new-feature
```

### Hotfix Workflow
```bash
# Create hotfix branch from main
git checkout main
git pull origin main
git checkout -b hotfix/critical-bug

# Fix bug and commit
git add .
git commit -m "Fix critical bug"

# Push and merge
git push -u origin hotfix/critical-bug
# Create PR/MR, then merge
```

### Release Workflow
```bash
# Create release branch
git checkout -b release/v1.0.0

# Finalize release
git add .
git commit -m "Prepare release v1.0.0"

# Tag release
git tag -a v1.0.0 -m "Release version 1.0.0"

# Push release
git push origin release/v1.0.0
git push origin v1.0.0
```

---

## Tips & Best Practices

### Commit Messages
- Use present tense ("Add feature" not "Added feature")
- Keep first line under 50 characters
- Add detailed description after blank line if needed
- Reference issue numbers when applicable

### Branch Naming
- `feature/description` - for new features
- `bugfix/description` - for bug fixes
- `hotfix/description` - for urgent fixes
- `release/version` - for releases

### Safety Tips
- Always pull before pushing
- Use `--force-with-lease` instead of `--force`
- Test before committing
- Use meaningful commit messages
- Create backups of important work

---

## Emergency Commands

### Recover lost commits
```bash
git reflog                   # Find lost commits
git cherry-pick <commit>     # Recover specific commit
git reset --hard <commit>    # Reset to lost commit
```

### Fix merge conflicts
```bash
git status                   # See conflicted files
# Edit files to resolve conflicts
git add <resolved-files>     # Stage resolved files
git commit                   # Complete merge
```

### Recover deleted branch
```bash
git reflog                   # Find branch commit
git checkout -b <branch-name> <commit-hash>
```

---

*Remember: When in doubt, `git status` is your best friend! 🎯*
