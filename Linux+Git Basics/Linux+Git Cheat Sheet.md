# ⚡ Linux & Git Quick Reference Cheat Sheet

## 🐧 Linux Commands Quick Ref

### Navigation
```bash
pwd                   # Print working directory
cd /path              # Change directory
cd ~                  # Home directory
cd ..                 # Parent directory
cd -                  # Previous directory
ls -lah               # List with details and hidden files
tree                  # Directory tree view
```

### File Operations
```bash
touch file.txt        # Create file
cat file.txt          # Show file contents
less file.txt         # View with pagination
head -n 20 file.txt   # First 20 lines
tail -n 20 file.txt   # Last 20 lines
```

### Copy, Move, Remove
```bash
cp source dest        # Copy
cp -r dir1 dir2       # Copy directory
mv source dest        # Move/rename
rm file.txt           # Remove
rm -r directory/      # Remove directory
```

### Search
```bash
find /path -name "*.txt"      # Find files
grep "pattern" file.txt       # Search in file
grep -r "pattern" /path       # Recursive search
```

### Permissions
```bash
chmod 644 file        # rw-r--r--
chmod 755 file        # rwxr-xr-x
chmod 700 file        # rwx------
chmod u+x file        # Add execute for user
chown user:group file # Change owner
```

### System Info
```bash
whoami                # Current user
df -h                 # Disk space
free -h               # Memory usage
top                   # Process monitor
ps aux                # List processes
ps aux | grep python  # Find process
```

### Processes
```bash
command &             # Run in background
jobs                  # List background jobs
fg %1                 # Bring to foreground
kill PID              # Terminate process
kill -9 PID           # Force kill
Ctrl+C                # Stop current process
Ctrl+Z                # Suspend process
```

### Package Management (APT)
```bash
sudo apt update       # Update package list
sudo apt upgrade      # Upgrade packages
sudo apt install pkg  # Install package
sudo apt remove pkg   # Remove package
sudo apt search pkg   # Search package
apt list --installed  # List installed
```

### Text Processing
```bash
sort file.txt         # Sort lines
uniq file.txt         # Remove duplicates
cut -d',' -f1 file    # Extract field
grep "text" file      # Search
sed 's/old/new/g'     # Replace text
awk '{print $1}'      # Print column
```

---

## 🔗 Git Commands Quick Ref

### Setup
```bash
git config --global user.name "Name"
git config --global user.email "email@example.com"
git config --list    # View config
```

### Initialize & Clone
```bash
git init              # Create new repo
git clone URL         # Clone repository
git clone URL folder  # Clone to folder
```

### Status & Changes
```bash
git status            # Show status
git diff              # Show changes
git diff --staged     # Show staged changes
git log --oneline     # Show history
```

### Staging & Committing
```bash
git add file.txt      # Stage file
git add .             # Stage all
git add -p            # Interactive staging
git commit -m "msg"   # Commit
git commit --amend    # Modify last commit
```

### Branching
```bash
git branch            # List branches
git branch -a         # List all branches
git branch feature    # Create branch
git checkout feature  # Switch branch
git checkout -b new   # Create and switch
git merge feature      # Merge branch
git branch -d feature # Delete branch
```

### Remote & GitHub
```bash
git remote -v         # Show remotes
git remote add origin URL
git push              # Push to GitHub
git push -u origin main
git pull              # Pull from GitHub
git fetch             # Download changes
git push origin --delete branch
```

### Undoing Changes
```bash
git restore file.txt              # Discard changes
git restore --staged file.txt     # Unstage
git reset --soft HEAD~1           # Undo last commit
git reset --hard HEAD~1           # Discard last commit
git revert HASH                   # Create undo commit
```

### Stashing
```bash
git stash             # Save changes
git stash pop         # Apply and remove
git stash list        # Show stashes
git stash drop        # Delete stash
```

### Useful Aliases
```bash
git config --global alias.st status
git config --global alias.co checkout
git config --global alias.br branch
git config --global alias.ci commit
git config --global alias.unstage 'restore --staged'
git config --global alias.last 'log -1 HEAD'
git config --global alias.visual 'log --graph --oneline --all'
```

---

## 📊 Permission Mode Reference

| Mode | Symbolic | Use Case |
|------|----------|----------|
| 777 | rwxrwxrwx | Everyone full access |
| 755 | rwxr-xr-x | Executables, scripts |
| 750 | rwxr-x--- | Team tools |
| 700 | rwx------ | Personal files |
| 644 | rw-r--r-- | Documents |
| 640 | rw-r----- | Team files |
| 600 | rw------- | Private files |

---

## 🔄 Common Workflows

### Feature Branch Workflow
```bash
git checkout main
git pull origin main
git checkout -b feature/auth

# Make changes, commit
git commit -m "Add authentication"

# Push and create PR
git push -u origin feature/auth

# After PR approval:
git checkout main
git pull
git branch -d feature/auth
```

### Keep Fork Updated
```bash
git fetch upstream
git merge upstream/main
git push origin main
```

### Undo Last Commit (Keep Changes)
```bash
git reset --soft HEAD~1
git add .
git commit -m "New message"
```

### Squash Commits
```bash
git rebase -i HEAD~3  # Last 3 commits
# Change 'pick' to 'squash' for commits to combine
```

---

## 🎯 Git Workflow Decision Tree

```
Need to make changes?
│
├─→ On main branch?
│   └─→ CREATE FEATURE BRANCH FIRST!
│       git checkout -b feature/name
│
├─→ Made changes?
│   └─→ git add .
│       git commit -m "message"
│
├─→ Want to push?
│   └─→ git push -u origin branch-name (first time)
│       git push (subsequent times)
│
├─→ Ready to merge?
│   └─→ Create Pull Request on GitHub
│       Get review and approval
│       Merge on GitHub
│
└─→ Merge conflicts?
    └─→ Edit files to resolve
        git add resolved-files
        git commit -m "Resolve conflicts"
```

---

## ⚠️ Dangerous Commands (Use Carefully!)

```bash
# These PERMANENTLY delete data:
rm -rf /           # Don't do this!
git reset --hard   # Discards all changes
git push --force   # Rewrites remote history
git branch -D      # Force delete branch
```

**Safe alternatives:**
- Use `git restore` instead of `rm`
- Use `git revert` instead of `git reset --hard`
- Use `git reset --soft` to undo safely

---

## 🐛 Troubleshooting Quick Fixes

| Problem | Solution |
|---------|----------|
| Detached HEAD | `git checkout main` |
| Forgot to commit | `git commit -am "msg"` |
| Wrong branch | Create another commit; revert latter |
| Merge conflict | Edit files, resolve, `git add .`, `git commit` |
| Lost commits | `git reflog` and `git checkout HASH` |
| Pushed wrong place | Use `git push origin HEAD:correct-branch` |

---



