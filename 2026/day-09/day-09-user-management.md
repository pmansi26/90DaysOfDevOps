# Day 09 Challenge

## Users & Groups Created
- Users: tokyo, berlin, professor, nairobi
- Groups: developers, admins, project-team

## Group Assignments
- developers :- tokyo , berlin
- admins :- berlin , professor
- project-team :- tokyo , nairobi

## Directories Created
- drwxrwsr-x 2 root developers   4096 Feb  7 13:27 dev-project
- drwxrwsr-x 2 root project-team 4096 Feb  7 13:36 team-workspace

## Commands Used
```bash
adduser tokyo
adduser berlin
adduser professor
cat /etc/passwd
groupadd developers
groupadd admins
cat etc/group
usermod -aG developers tokyo
usermod -aG developers,admin berlin
usermod -aG admin professor
mkdir /opt/dev-project
chgrp developers /opt/dev-project
chmod 2775 dev-project
adduser nairobi
groupadd project-team
usermod -aG project-team tokyo
usermod -aG project-team nairobi
mkdir /opt/team-workspace
chmod 2775 team-workspace
```


## What I Learned
1. To inherit the permissions of a directory to the files we have to set group id also by using to command
   #chmod 2775 dev-project
2. I have learned how to change group ownership of a file or directory using chgrp command
3. I have learned how to verify the file permissions of a file by switching the users and trying to read or write a file
# Issue While Creating User berlin
## Problem
While creating users with adduser, the warning “waiting for a lock to become available” was encountered when creating user berlin.
## Cause
The adduser process for user tokyo was suspended using Ctrl + Z, leaving a stopped process holding the lock.
## Fix
Stopped adduser processes were identified and terminated, after which the adduser berlin command worked successfully.
## Lesson Learned
Press ENTER to skip optional fields, use Ctrl + C to cancel, and avoid Ctrl + Z during user creation.
