# Day 10 – File Permissions & File Operations Challenge
## Files Created
- devops.txt
- notes.txt
- script.sh

## Permission Changes
- script.sh
``` bash
### before
-rw-rw-r-- 1 ubuntu ubuntu 20 Feb 11 09:20 script.sh
### after
-rwxrwxr-x 1 ubuntu ubuntu 20 Feb 11 09:20 script.sh
```
- devops.txt
``` bash
### before
-rw-rw-r-- 1 ubuntu ubuntu  0 Feb 11 09:19 devops.txt
### after
-r--r--r-- 1 ubuntu ubuntu  0 Feb 11 09:19 devops.txt
```
- notes.txt
``` bash
### before
-rw-rw-r-- 1 ubuntu ubuntu 37 Feb 11 09:20 notes.txt
### after
-rw-r----- 1 ubuntu ubuntu 37 Feb 11 09:20 notes.txt
```
- prject directory
``` bash
### before
drwxrwxr-x 2 ubuntu ubuntu 4096 Feb 11 09:24 project
### after
drwxr-xr-x 2 ubuntu ubuntu 4096 Feb 11 09:24 project
```
## Commands Used
``` bash
  1  ls
    2  ls -a
    3  touch devops.txt
    4  ls
    5  echo "this is file created by echo command" > notes.txt
    6  ls
    7  cat notes.txt
    8  vim script.sh
    9  ls -l
   10  cat notes.txt
   11  cat /etc/passwd | head -n 5
   12  cat /etc/passwd | tail -n 5
   13  ls -l
   14  chmod +x script.sh
   15  ls -l
   16  ./script.sh
   17  chmod -w devops.txt
   18  ls -l
   19  chmod 640 notes.txt
   20  ls -l
   21  mkdir project/
   22  ls -l
   23  chmod 755 project
   24  ls -l
   25  echo "trying to edit to a read only file" > devops.txt
   26  history
```

## What I Learned
- When I tried to edit a read only file I will get a permission denied error.
- To execute my shell script I have to first add +x permission using chmod command
