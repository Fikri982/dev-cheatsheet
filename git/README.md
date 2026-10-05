# 🔀 Git Cheatsheet

Quick reference for commonly used Git commands and workflows.

## 📁 Navigation

- [Configuration](#configuration)
- [Repository](#repository)
- [Changes](#changes)
- [Commit](#commit)
- [Branch](#branch)
- [Remote](#remote)
- [Sync](#sync)
- [Undo Changes](#undo-changes)
- [Stash](#stash)
- [Useful Commands](#useful-commands)

---

## Configuration

### Check Git version

```bash
git --version
```

### Check configuration

```bash
git config --list
```

### Set username

```bash
git config --global user.name "Your Name"
```

### Set email

```bash
git config --global user.email "you@example.com"
```

---

## Repository

### Initialize repository

```bash
git init
```

### Clone repository

```bash
git clone <repository-url>
```

### Check repository status

```bash
git status
```

---

## Changes

### View changes

```bash
git diff
```

### Stage a file

```bash
git add <file>
```

### Stage everything

```bash
git add .
```

### View staged changes

```bash
git diff --staged
```

---

## Commit

### Create commit

```bash
git commit -m "commit message"
```

### View commit history

```bash
git log
```

Compact:

```bash
git log --oneline
```

---

## Branch

### List branches

```bash
git branch
```

### Create branch

```bash
git branch <branch-name>
```

### Switch branch

```bash
git switch <branch-name>
```

### Create and switch

```bash
git switch -c <branch-name>
```

### Delete branch

```bash
git branch -d <branch-name>
```

---

## Remote

### View remote

```bash
git remote -v
```

### Add remote

```bash
git remote add origin <repository-url>
```

### Change remote URL

```bash
git remote set-url origin <repository-url>
```

---

## Sync

### Fetch remote changes

```bash
git fetch
```

### Pull changes

```bash
git pull
```

### Push branch

```bash
git push
```

First push:

```bash
git push -u origin <branch-name>
```

### Push all branches

```bash
git push --all
```

---

## Undo Changes

### Unstage file

```bash
git restore --staged <file>
```

### Discard changes in working directory

```bash
git restore <file>
```

### Amend last commit

```bash
git commit --amend
```

> ⚠️ Be careful when amending commits that have already been pushed.

---

## Stash

### Save current changes

```bash
git stash
```

### List stashes

```bash
git stash list
```

### Apply latest stash

```bash
git stash pop
```

### Remove a stash

```bash
git stash drop
```

---

## Useful Commands

| Command             | Purpose                   |
| ------------------- | ------------------------- |
| `git status`        | Check repository status   |
| `git add .`         | Stage changes             |
| `git commit`        | Create commit             |
| `git log --oneline` | View compact history      |
| `git branch`        | List branches             |
| `git switch`        | Switch branch             |
| `git fetch`         | Download remote changes   |
| `git pull`          | Fetch + integrate changes |
| `git push`          | Upload commits            |
| `git diff`          | View unstaged changes     |
| `git restore`       | Restore changes           |
| `git stash`         | Temporarily save changes  |
