# 🐧 Linux Command Cheat Sheet
## File & Directory Management
- `ls` → List files and directories  
- `ls -l` → Detailed file listing  
- `pwd` → Show current directory path  
- `cd <dir>` → Change directory  
- `mkdir <dir>` → Create a directory  
- `rmdir <dir>` → Delete empty directory  
- `rm <file>` → Remove a file  
- `rm -r <dir>` → Remove directory recursively  
- `cp src dest` → Copy files or directories  
- `mv src dest` → Move or rename files  

---

##  File Viewing & Editing
- `cat <file>` → Display file content  
- `less <file>` → View file page by page  
- `head <file>` → Show first 10 lines  
- `tail <file>` → Show last 10 lines  
- `nano <file>` → Edit file using nano editor  
- `vim <file>` → Edit file using vim  

---

##  Process Management
- `ps aux` → Show all running processes  
- `top` → Live process monitoring  
- `htop` → Interactive process viewer  
- `kill PID` → Terminate a process  
- `nice -n 10 cmd` → Start process with lower priority  
- `renice 5 -p PID` → Change priority of running process  
- `bg` → Resume stopped job in background  
- `fg` → Bring job to foreground  

---

##  Permissions & Ownership
- `chmod 755 file` → Change file permissions  
- `chown user:group file` → Change file ownership  
- `umask` → Show default permission settings  

---

##  Networking Commands
- `ping <host>` → Check network connectivity  
- `ip addr` → Display IP addresses  
- `curl <url>` → Fetch data from a URL  

---

##  System & Disk Information
- `df -h` → Disk usage in human-readable format  
- `du -sh <dir>` → Directory size  
- `free -h` → Memory usage  
- `uptime` → System running time  

---

##  Job Control & History
- `jobs` → List background jobs  
- `history` → Show command history  
- `clear` → Clear terminal screen  

---
## Important for troubleshooting
### listing top 5 processes with highest cpu usage
-`ps -eo pid,user,%cpu,%mem,comm --sort=-%cpu | head -n 6`
### Listing top 5 disk usage
-`du -xh --max-depth=1 / 2>/dev/null | sort -hr | head -n 5`


---
