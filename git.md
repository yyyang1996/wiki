---
title: Git
date: '2020-11-25T18:28:43.000Z'
icon: icon-git
background: bg-gray-400
tags:
  - github
  - gitlab
  - version
  - VCS
categories:
  - Linux Command
intro: >-
  This cheat sheet summarizes commonly used Git command line instructions for
  quick reference.
---

# git

## Getting Started

### Create a Repository

Create a new local repository 

```bash
$ git init \[project name\]
```

Clone a repository 
``` shell
$ git clone git_url
```

Clone a repository into a specified directory 

```bash
$ git clone git\_url my\_directory
```

### Make a change
Show modified files in working directory, staged for your next commit
``` shell
$ git status
```

Stages the file, ready for commit 

```bash
$ git add \[file\]
```

Stage all changed files, ready for commit
``` shell
$ git add .
```

Commit all staged files to versioned history 

```bash
$ git commit -m "commit message"
```

Commit all your tracked files to versioned history
``` shell
$ git commit -am "commit message"
```

Unstages file, keeping the file changes 

```bash
$ git reset \[file\]
```

Revert everything to the last commit
``` shell
$ git reset --hard
```

Diff of what is changed but not staged 

```bash
$ git diff
```

Diff of what is staged but not yet commited
``` shell
$ git diff --staged
```

Apply any commits of current branch ahead of specified one 

```bash
$ git rebase \[branch\]
```

### Configuration

Set the name that will be attached to your commits and tags
``` shell
$ git config --global user.name "name"
```

Set an email address that will be attached to your commits and tags 

```bash
$ git config --global user.email "email"
```

Enable some colorization of Git output
``` shell
$ git config --global color.ui auto
```

Edit the global configuration file in a text editor 

```bash
$ git config --global --edit
```

### Working with Branches

List all local branches
``` shell
$ git branch
```

List all branches, local and remote 

```bash
$ git branch -av
```

Switch to a branch, my_branch, and update working directory
``` shell
$ git checkout my_branch
```

Create a new branch called new\_branch 

```bash
$ git branch new\_branch
```

Delete the branch called my_branch
``` shell
$ git branch -d my_branch
```

Merge branchA into branchB 

```bash
$ git checkout branchB $ git merge branchA
```

Tag the current commit
``` shell
$ git tag my_tag
```

### Observe your Repository

Show the commit history for the currently active branch 

```bash
$ git log
```

Show the commits on branchA that are not on branchB
``` shell
$ git log branchB..branchA
```

Show the commits that changed file, even across renames 

```bash
$ git log --follow \[file\]
```

Show the diff of what is in branchA that is not in branchB
``` shell
$ git diff branchB...branchA
```

Show any object in Git in human-readable format 

```bash
$ git show \[SHA\]
```

### Synchronize

Fetch down all the branches from that Git remote
``` shell
$ git fetch [alias]
```

Merge a remote branch into your current branch to bring it up to date 

```bash
$ git merge \[alias\]/\[branch\]
```

Transmit local branch commits to the remote repository branch
``` shell
$ git push [alias] [branch]
```

Fetch and merge any commits from the tracking remote branch 

```bash
$ git pull
```

Merge just one specific commit from another branch to your current branch
``` shell
$ git cherry-pick [commit_id]
```

### Remote

Add a git URL as an alias 

```bash
$ git remote add \[alias\] \[url\]
```

Show the names of the remote repositories you've set up
``` shell
$ git remote
```

Show the names and URLs of the remote repositories 

```bash
$ git remote -v
```

Remove a remote repository
``` shell
$ git remote rm [remote repo name]
```

Change the URL of the git repo 

```bash
$ git remote set-url origin \[git\_url\]
```

### Temporary Commits

Save modified and staged changes
``` shell
$ git stash
```

List stack-order of stashed file changes 

```bash
$ git stash list
```

Write working from top of stash stack
``` shell
$ git stash pop
```

Discard the changes from top of stash stack 

```bash
$ git stash drop
```

### Tracking path Changes
Delete the file from project and stage the removal for commit
``` shell
$ git rm [file]
```

Change an existing file path and stage the move 

```bash
$ git mv \[existing-path\] \[new-path\]
```

Show all commit logs with indication of any paths that moved
``` shell
$ git log --stat -M
```

### Ignoring Files

/logs/*

!logs/.gitkeep

/# Ignore Mac system files
.DS_store

# Ignore node_modules folder
node_modules

# Ignore SASS config files
.sass-cache
```

A `.gitignore` file specifies intentionally untracked files that Git should ignore

## Tricks

### Rename branch

* **Renamed to `new_name`**

```bash

$ git branch -m

```

* **Push and reset**

```bash

$ git push origin -u

```

* **Delete remote branch**

```bash

$ git push origin --delete

```

  {.style-timeline}

### Log

Search change by content 
```bash
$ git log -S''
```

Show changes over time for specific file
```shell
$ git log -p <file_name>
```

Print out a cool visualization of your log 
```bash
$ git log --pretty=oneline --graph --decorate --all
```

### Branch
List all branches and their upstreams 
```shell
$ git branch -vv
```

Quickly switch to the previous branch 
```bash
$ git checkout -
```

Get only remote branches
```shell
$ git branch -r
```

Checkout a single file from another branch 
```bash
$ git checkout --
```

### Commit
Rewrite last commit message
```shell
$ git commit -v --amend
```

### Git Aliases

```bash
git config --global alias.co checkout
git config --global alias.br branch
git config --global alias.ci commit
git config --global alias.st status
```

See also: [More Aliases](https://gist.github.com/johnpolacek/69604a1f6861129ef088)

