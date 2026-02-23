# Task 1
## 1.What is a branch in Git?
- A branch is a separate line of development in a repository
- It lets you work on new features or fixes without affecting the main code
- Each branch has its own commits
## 2.Why do we use branches instead of committing everything to main?
- Branches keep the main branch stable and production-ready
- Developers can work on features independently
- It allows testing and review before merging changes into main
## 3.What is HEAD in Git?
- HEAD is a pointer that shows your current branch or current commit
- It tells Git where you are working right now
- When you switch branches, HEAD moves to that branch
## 4.What happens to your files when you switch branches?
- Git updates your working directory to match the selected branch
- Files may change, appear, or disappear based on that branch’s commits
- Uncommitted changes may stay or cause conflicts if they overlap with the new branch
# Task 2
## 1.List all branches in your repo
``` bash
$ git branch
* master
```
## 2.Create a new branch called feature-1
``` bash
$ git branch feature-1
$ git branch
   feature-1
* master
```
## 3.Switch to feature-1
``` bash
$ git switch feature-1
Switched to branch 'feature-1'
```
## 4.Create a new branch and switch to it in a single command — call it feature-2
``` bash
$ git checkout -b feature-2
Switched to a new branch 'feature-2'
```
## 5.Try using git switch to move between branches — how is it different from git checkout?
- checkout is used to create new branch and switch between to it while switch is used to switch to branch that is already existing.
## 6.Make a commit on feature-1 that does not exist on main
``` bash
$ vim feature-1.txt
$ git add feature-1.txt
$ git commit -m "chore: added feature-1.txt"
$ git log --oneline
8136f72 (HEAD -> feature-1) chore: added feature-1.txt
3344d93 (master, feature-2) chore: added branching commands
ec2e00f chore: added usage of git rm command
a95d7f7 feat: added git-commands.md file
ab7eaf5 chore: Added README.md file
```
## 7.Switch back to main — verify that the commit from feature-1 is not there
- Yes,not there
``` bash
3344d93 (HEAD -> master, feature-2) chore: added branching commands
ec2e00f chore: added usage of git rm command
a95d7f7 feat: added git-commands.md file
ab7eaf5 chore: Added README.md file
```
## 8.Delete a branch you no longer need
``` bash
$ git branch -D feature-2
Deleted branch feature-2 (was 3344d93)
```
# Task 3
## 1.Create a new repository on GitHub (do NOT initialize it with a README)
- Created new repository named devops-git-practise without README.md on remote
## 2.Connect your local devops-git-practice repo to the GitHub remote
Steps to connect local devops-git-practice repo to the github remote
1 Generated ssh on local using command ssh-keygen
2 Copied public key and placed on the github under ssh keys 
4 Copied the ssh url of the repo
5 Setted the origin url using command git remote set-url origin git@github.com:pmansi26/devops-git-practice.git
## 3.Push your main branch to GitHub
``` bash
 git push origin master
The authenticity of host 'github.com (140.82.112.4)' can't be established.
ED25519 key fingerprint is SHA256:+DiY3wvvV6TuJJhbpZisF/zLDA0zPMSvHdkr4UvCOqU.
This key is not known by any other names.
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
Warning: Permanently added 'github.com' (ED25519) to the list of known hosts.
Enumerating objects: 15, done.
Counting objects: 100% (15/15), done.
Delta compression using up to 2 threads
Compressing objects: 100% (14/14), done.
Writing objects: 100% (15/15), 2.03 KiB | 2.03 MiB/s, done.
Total 15 (delta 3), reused 0 (delta 0), pack-reused 0
remote: Resolving deltas: 100% (3/3), done.
To github.com:pmansi26/devops-git-practice.git
 * [new branch]      master -> master
```
## 4.Push feature-1 branch to GitHub4
``` bash
$ git push origin feature-1
Enumerating objects: 4, done.
Counting objects: 100% (4/4), done.
Delta compression using up to 2 threads
Compressing objects: 100% (3/3), done.
Writing objects: 100% (3/3), 386 bytes | 386.00 KiB/s, done.
Total 3 (delta 0), reused 0 (delta 0), pack-reused 0
remote:
remote: Create a pull request for 'feature-1' on GitHub by visiting:
remote:      https://github.com/pmansi26/devops-git-practice/pull/new/feature-1
remote:
To github.com:pmansi26/devops-git-practice.git
 * [new branch]      feature-1 -> feature-1
```
## 5.Verify both branches are visible on GitHub
- changes are visbile
## 6. What is the difference between origin and upstream?
### Origin
- origin is the default name of the remote repository you cloned or connected your local repo to
- It usually points to your own GitHub repository where you push your changes
### Upstream
- upstream is another remote that usually points to the original repository (for example, the main project you forked from)
- It is used to pull updates from the original source
# Task 4
- Made changes from the remote in the git-commands.md file
## 2.Pull that change to your local repo
``` bash
ubuntu@ip-172-31-21-107:~/devops-git-practice$ git pull origin master
remote: Enumerating objects: 8, done.
remote: Counting objects: 100% (8/8), done.
remote: Compressing objects: 100% (6/6), done.
remote: Total 6 (delta 2), reused 0 (delta 0), pack-reused 0 (from 0)
Unpacking objects: 100% (6/6), 2.21 KiB | 755.00 KiB/s, done.
From github.com:pmansi26/devops-git-practice
 * branch            master     -> FETCH_HEAD
   7fac038..e28194b  master     -> origin/master
Updating 7fac038..e28194b
Fast-forward
 git-commands.md | 12 ++++++++++++
 1 file changed, 12 insertions(+)
```
## 3.What is the difference between git fetch and git pull?
### git fetch
- git fetch downloads the latest changes from the remote repository but does not merge them into your current branch
- It lets you see what changed before updating your code
### git pull
- git pull downloads the latest changes from the remote and automatically merges them into your current branch
- It updates your local working code immediately
# Task 6
## 1.What is the difference between clone and fork?
- git clone creates a copy of a repository on your local machine so you can work on it
- fork creates a copy of someone else’s repository under your own GitHub account
- Clone = local copy
- Fork = your own remote copy on GitHub
## 2.When would you clone vs fork?
- Use clone when you have direct access to the repository and want to work locally
- Use fork when you don’t have write access and want to contribute to someone else’s project
- Typical workflow:
fork → clone your fork → make changes → create pull request
## 3.After forking, how do you keep your fork in sync with the original repo?
- we ca use sync fork to keep our in sync with the original repo
