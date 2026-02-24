# Task 1
## 1.What is a fast-forward merge?
- A fast-forward merge happens when the target branch has no new commits after the feature branch was created
- Git simply moves the branch pointer forward to the latest commit
- No merge commit is created
## 2.When does Git create a merge commit instead?
- Git creates a merge commit when both branches have new commits (they diverged)
- Git needs to combine two different histories
- A new commit is created to join both branches
## 3.What is a merge conflict?
- A merge conflict happens when Git cannot automatically decide how to combine changes
- Usually occurs when the same file and same line are edited in different branches
- Git asks you to resolve it manually
### Commands used 
``` bash
 git switch master
 git merge feature-login
 git log --oneline
 git checkout -b feature-signup
 git switch master
 git merge feature-signup
 git log --oneline
```
# Task 2
## 1.What does rebase actually do to your commits?
- Rebase moves your commits on top of another branch’s latest commit
- Git replays your commits one by one as if they were created later
- This creates a cleaner, linear history
- It rewrites commit history
## 2.How is the history different from a merge?
- Merge keeps both branch histories and creates a merge commit
- Rebase rewrites commits so history looks straight (no merge commit)
- Merge = history with branches
- Rebase = linear history
## 3.Why should you never rebase commits that have been pushed and shared with others?
- Rebase changes commit IDs (history is rewritten)
- Other developers may already have the old commits
- This causes conflicts and confusion when pulling
- It can break collaboration
## 4.When would you use rebase vs merge?
### Use rebase
- To keep history clean
- Before pushing your feature branch
- To update your branch with latest main changes
### Use merge
- When working on shared branches
- When you want to preserve history
- For final integration into main
# Task 3
## 1.What does squash merging do?
- Squash merging combines all commits from a feature branch into one single commit
- Instead of keeping multiple small commits, Git creates one clean commit on the target branch
- It simplifies project history
## 2.When would you use squash merge vs regular merge?
### Use squash merge
- When a feature branch has many small or messy commits
- When you want a clean and readable history
- Common in pull request workflows
### Use regular merge
- When you want to preserve full commit history
- When working on shared branches
- When commit-level traceability is important
### What is the trade-off of squashing?
- You lose detailed commit history from the feature branch
- It becomes harder to see step-by-step changes
- Debugging specific commits later can be difficult
# Task 4
## 1.What is the difference between git stash pop and git stash apply?
- git stash pop restores the stashed changes and removes that stash entry from the stash list
- git stash apply restores the stashed changes but keeps the stash entry in the list so you can reuse it later
-  pop = apply + delete
- pply = apply only
## 2.When would you use stash in a real-world workflow?
- When you need to switch branches but your work is incomplete
- When pulling latest changes without committing half-done work
- During debugging or hotfix tasks where you temporarily pause current work
- When testing something quickly and you don’t want a temporary commit
# Task 5
## 1.What does cherry-pick do?
- Cherry-pick copies a specific commit from one branch and applies it to another branch
- It brings only selected changes instead of merging the entire branch
- A new commit is created with a different commit ID
## 2.When would you use cherry-pick in a real project?
-To apply a bug fix from a feature branch to production quickly
-To backport fixes to older release branches
## 3.When you need only one change from another branch without merging everything
- During hotfix scenarios
- What can go wrong with cherry-picking?
- It can cause merge conflicts if the same code was changed elsewhere
- Duplicate commits may appear in history
- Important context from the original branch may be missed
- Overusing cherry-pick can make history confusing
