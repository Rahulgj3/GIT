# Git and GitHub Comprehensive Guide

## 1. What is Git?
Git is a **distributed version control system** that helps developers track changes in their codebase, collaborate with teams, and manage project versions efficiently.

### Key Features:
- Tracks changes in files over time.
- Enables multiple developers to work on a project simultaneously.
- Supports branches for experimentation and merging.
- Works locally and remotely.

## 2. What is GitHub?
GitHub is a cloud-based platform that provides **Git repository hosting** services with additional collaboration features like issue tracking, pull requests, and CI/CD integration.

### Key Features:
- Online storage for Git repositories.
- Code collaboration and review through pull requests.
- Integration with DevOps workflows.
- Issue tracking, project management, and CI/CD pipelines.

---

## 3. Git Configuration

### Where is the Git Config File Stored in Linux?
Git stores its configuration settings in different locations:
- **System-wide configuration**: `/etc/gitconfig`
- **User-specific configuration**: `~/.gitconfig` or `~/.config/git/config`
- **Repository-specific configuration**: `.git/config` (inside a Git repo)

### Sample Git Config File
```ini
[user]
    name = John Doe
    email = johndoe@example.com

[core]
    editor = nano
    autocrlf = input

[alias]
    co = checkout
    ci = commit
    st = status
```

---

## 4. Git Setup and Configuration Commands

### Install Git
#### On Ubuntu/Debian:
```bash
sudo apt update
sudo apt install git
```

#### On macOS:
```bash
brew install git
```

#### On Windows:
[Download Git](https://git-scm.com/downloads) and install.

### Verify Installation:
```bash
git --version
```

### Configure Git for a User
```bash
git config --global user.name "John Doe"
git config --global user.email "johndoe@example.com"
```

### Check Configuration
```bash
git config --list
```

### Change Configurations
```bash
git config --global core.editor nano
```

---

## 5. Connecting Git to GitHub

### Using HTTPS Authentication
```bash
git remote add origin https://github.com/username/repository.git
```

### Using SSH Authentication
#### Step 1: Generate SSH Key
```bash
ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
```

#### Step 2: Start SSH Agent and Add Key
```bash
eval "$(ssh-agent -s)"
ssh-add ~/.ssh/id_rsa
```

#### Step 3: Copy Public Key to GitHub
```bash
cat ~/.ssh/id_rsa.pub
```
- Copy the key and add it to GitHub under **Settings → SSH and GPG keys**.

#### Step 4: Test Connection
```bash
ssh -T git@github.com
```

### Check Which Remote URL is Being Used
```bash
git remote -v
```

---

## 6. Cloning a Repository
```bash
git clone https://github.com/username/repository.git
```
OR using SSH:
```bash
git clone git@github.com:username/repository.git
```

---

## 7. Adding Files and Making a Commit
```bash
cd repository/
touch newfile.txt
```

```bash
git add newfile.txt
```

```bash
git commit -m "Added newfile.txt"
```

---

## 8. Pushing and Pulling Changes
### Push to GitHub
```bash
git push origin main
```

### Pull Changes from GitHub
```bash
git pull origin main
```

---

## 9. Branching and Merging
### Create a New Branch
```bash
git checkout -b feature-branch
```

### Switch to an Existing Branch
```bash
git checkout main
```

### Merge a Branch
```bash
git merge feature-branch
```

### Delete a Branch
```bash
git branch -d feature-branch
```

---

## 10. Reverting and Resetting
### Undo Last Commit (Keep Changes)
```bash
git reset --soft HEAD~1
```

### Undo Last Commit (Remove Changes)
```bash
git reset --hard HEAD~1
```

### Remove a File from Git
```bash
git rm file.txt
```

---

## 11. Git Protocols and Ports
| Protocol | URL Format | Port |
|----------|------------------------------------|------|
| HTTPS    | https://github.com/user/repo.git  | 443  |
| SSH      | git@github.com:user/repo.git      | 22   |
| Git      | git://github.com/user/repo.git    | 9418 |

---

## 12. Common Issues and Troubleshooting

### 1. Authentication Errors
#### Solution:
- Ensure correct SSH key is added to GitHub.
- Check Git credential helper:
```bash
git credential reject https://github.com
```

### 2. Permission Denied (SSH)
#### Solution:
```bash
ssh-add ~/.ssh/id_rsa
```

### 3. Merge Conflicts
#### Solution:
```bash
git mergetool
```
Manually resolve conflicts and commit.

---

## 13. Advanced Git Topics
### 1. Stashing Changes
```bash
git stash
```
```bash
git stash apply
```

### 2. Rebasing
```bash
git rebase main
```

### 3. Cherry Picking
```bash
git cherry-pick <commit-hash>
```

### 4. Git Hooks
```bash
.git/hooks/pre-commit
```

---

## 14. Tips and Tricks
- Use `git log --oneline` for a concise commit history.
- Enable auto-correction for commands:
```bash
git config --global help.autocorrect 1
```
- Set up global Git ignore:
```bash
echo "*.log" >> ~/.gitignore_global
git config --global core.excludesfile ~/.gitignore_global
```

---

## 15. Summary
This guide covered:
- Git and GitHub basics.
- Configuration and authentication.
- Branching, merging, and rebasing.
- Troubleshooting and advanced topics.
- Useful commands and best practices.

By mastering these concepts, you’ll be well-equipped to handle any Git-related tasks in a DevOps environment!


