# Task 1
## 1. Verify Git is installed on your machine
- verifited using command
  ``` bash
  git --verion
  version = 2.43.0
  ```
## 2.Set up your Git identity — name and email
- setted up my identity using the commands
  ``` bash
  git config user.name 'pmansi26'
  git config user.email 'pampadmansi3454@gmail.com'
  ``` 
## 3.Verify your configuration
- Verfication
  ``` bash
  user.name=pmansi26
  user.email=pampadmansi3454@gmail.com
  ```
# Task 2
## 1.Create a new folder called devops-git-practice
``` bash
mkdir devops-git-practice
```
## 2.Initialize it as a Git repository
``` bash
cd devops-git-practice
git init
```
## 3.Check the status — read and understand what Git is telling you
``` bash
On branch master

No commits yet

nothing to commit (create/copy files and use "git add" to track)
```
- git is saying that it is on branch "Master"
- There are no commit done yet and we can create a file add it using git add so that git can track it 
## 4.Explore the hidden .git/ directory — look at what's inside
``` bash
total 32
-rw-rw-r-- 1 ubuntu ubuntu   23 Feb 22 16:48 HEAD
drwxrwxr-x 2 ubuntu ubuntu 4096 Feb 22 16:48 branches
-rw-rw-r-- 1 ubuntu ubuntu   92 Feb 22 16:48 config
-rw-rw-r-- 1 ubuntu ubuntu   73 Feb 22 16:48 description
drwxrwxr-x 2 ubuntu ubuntu 4096 Feb 22 16:48 hooks
drwxrwxr-x 2 ubuntu ubuntu 4096 Feb 22 16:48 info
drwxrwxr-x 4 ubuntu ubuntu 4096 Feb 22 16:48 objects
drwxrwxr-x 4 ubuntu ubuntu 4096 Feb 22 16:48 refs
```
# Task 4
## 1.Stage your file
``` bash
vim README.md
git add README.md
git status
#status
On branch master

No commits yet

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        README.md

nothing added to commit but untracked files present (use "git add" to track)
```
## 3.Check what's staged
``` bash
On branch master

No commits yet

Changes to be committed:
  (use "git rm --cached <file>..." to unstage)
        new file:   README.md
```
## 4.Commit with a meaningful message
``` bash
git commit -m "chore: Added README.md file"
```
## 5.View your commit history
``` bash
commit ab7eaf52b7e1edd193f3b029863640fbc527cbc3 (HEAD -> master)
Author: Ubuntu <ubuntu@ip-172-31-21-107.ec2.internal>
Date:   Sun Feb 22 17:09:54 2026 +0000

    chore: Added README.md file
```
# Task 5
## Commit history in compact form
``` bash
3344d93 (HEAD -> master) chore: added branching commands
ec2e00f chore: added usage of git rm command
a95d7f7 feat: added git-commands.md file
ab7eaf5 chore: Added README.md file
```
# Task 6
## What is the difference between git add and git commit?
- git add adds a file to the staging area so that git can track it changes
- git commit makes a staged file to the tracked file
## What does the staging area do? Why doesn't Git just commit directly?
- The staging area lets you choose which changes should go into the next commit
- It helps you commit only selected files instead of everything you changed
- Git doesn’t commit directly so developers can organize changes properly
## What information does git log show you?
- commit id (unique hash)
- author name
- date and time of commit
- commit message
- history of changes over time
## What is the .git/ folder and what happens if you delete it?
- The .git/ folder stores all repository data like commits, branches, and configuration
- It is the internal database of Git
- If you delete .git/, your project becomes a normal folder and all Git history is lost
## What is the difference between a working directory, staging area, and repository?
- Working directory → where you edit and create files
- Staging area → where you prepare selected changes using git add
- Repository → where committed changes are saved permanently
- Flow:
Working directory → Staging area → Repository


