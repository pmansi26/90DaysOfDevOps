# Day 07 – Linux File System Hierarchy & Scenario-Based Practice
### Part 1: Linux File System Hierarchy
#### Core Directories (Must Know):

- / (root) – The top-level directory; everything in Linux starts from /, including system folders like bin, lib, etc, and tmp.
- /home – Contains home directories for normal users, where they store files and perform daily tasks.
- /root – The home directory of the root (administrator) user, not accessible to normal users.
- /etc – Stores system and application configuration files.
- /var/log – Contains system and application log files (very important for troubleshooting and DevOps).
- /tmp – Holds temporary files that are usually deleted automatically after reboot.

#### Additional Directories
- /bin – Contains essential system commands needed for basic operation (like ls, cp, cat).
- /usr/bin – Stores most user-level command binaries and utilities used in daily work.
- /opt – Holds optional or third‑party software installed manually or by vendors.

#### Hands-on task:
1.Find the largest log file in /var/log
``` bash
du -sh /var/log/* 2>/dev/null | sort -h | tail -5
Output:-
48K     /var/log/dmesg
60K     /var/log/kern.log
132K    /var/log/cloud-init.log
144K    /var/log/syslog
17M     /var/log/journal
```
2. Look at a config file in /etc
``` bash
cat /etc/hostname
Output:-
ip-172-31-17-87
```
3. Check your home directory
``` bash
ls -la ~
Output:-
total 36
drwxr-x--- 4 ubuntu ubuntu 4096 Feb  4 09:52 .
drwxr-xr-x 3 root   root   4096 Feb  4 09:20 ..
-rw-r--r-- 1 ubuntu ubuntu  220 Mar 31  2024 .bash_logout
-rw-r--r-- 1 ubuntu ubuntu 3771 Mar 31  2024 .bashrc
drwx------ 2 ubuntu ubuntu 4096 Feb  4 09:33 .cache
-rw-r--r-- 1 ubuntu ubuntu  807 Mar 31  2024 .profile
drwx------ 2 ubuntu ubuntu 4096 Feb  4 09:20 .ssh
-rw------- 1 ubuntu ubuntu 1160 Feb  4 09:52 .viminfo
-rw-rw-r-- 1 ubuntu ubuntu  687 Feb  4 09:52 notes.txt
```
### Part 2: Scenario-Based Practice 
Scenario 1: Service Not Starting
``` bash
A web application service called 'myapp' failed to start after a server reboot.
What commands would you run to diagnose the issue?
Write at least 4 commands in order.
```
Step 1 :- Checking service status 
``` bash
systemctl status myapp
```
While using this command its also important check the substate of the service like :-
|sub-state |Meaning |
|----------|---------|
|running   | Service is actively running |
|exited    | completed execution successfully|
|dead      | fully stopped |
|failed    | error occured |
| auto-restart | systemd is trying to restart the service|

Step 2 :- Check recent logs of the service 
``` bash
journalctl -u myapp -xe
```
Why:
- Displays detailed error logs
- Helps identify issues like port conflicts, missing files, permission errors, or config failures

Step 3:- Verify if the service is enabled on boot
``` bash
systemctl is-enalbled myapp
```
Why:
- Confirms whether the service is configured to start automatically after reboot
- If disabled, it won’t start even if it works manually

Step 4:- Validate the service configuration
``` bash
myapp --congiftest
```
Why:
- Configuration errors are a common cause of startup failure
- Reboot can expose misconfigurations (missing env vars, paths, etc.)

Scenario 2: High CPU Usage
``` bash
Your manager reports that the application server is slow.
You SSH into the server. What commands would you run to identify
which process is using high CPU?
```
Step 1 :- check overall CPU usage
``` bash
top or htop
```
- Real‑time CPU usage
- Processes sorted by CPU usage (default)
- %CPU column shows which process is consuming the most CPU

Step 2 :- Sort processes by CPU usage
``` bash
top -o %CPU
```
- Forces sorting by CPU (useful if sorting was changed)
- Helps immediately identify top CPU‑hungry processes

Step 3 :- Use ps for a quick snapshot
``` bash
ps -eo pid,ppid,cmd,%cpu,%mem --sort=-%cpu | head
```
- Lists processes sorted by CPU usage (highest first)
Scenario 3: Finding Service Logs
``` bash
A developer asks: "Where are the logs for the 'docker' service?"
The service is managed by systemd.
What commands would you use?
```
Step 1 :- Check serivce status
``` bash
systemctl status ssh
```
Step 2:- view the last 50 lines of ssh logs
``` bash
journalctl -u ssh -n 50
```
Step 3 :- Follow ssh logs in real time
``` bash
journalctl -u ssh -f
```
Scenario 4: File Permissions Issue
``` bash
A script at /home/user/backup.sh is not executing.
When you run it: ./backup.sh
You get: "Permission denied"

What commands would you use to fix this?
```
Step 1 :- check the file permissions
``` bash
ls -l /home/user/backup.sh
```
- This file must have x permission to make it executable add x permission if allowed
Step 2 :- adding x permission to the file
``` bash
chmod +x /home/user/backup.sh
```
- chmod command is used to add or remove permissions to the file

Step 3 :- Verify if the permission is added succesfully
``` bash
ls -l /home/user/backup.sh
```
- look for x

Step 4 :- Check wheather the file is executing now
``` bash
./backup.sh
```



