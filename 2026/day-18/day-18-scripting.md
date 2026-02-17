# Day 18 – Shell Scripting: Functions & Slightly Advanced Concepts
## Task-1
``` bash
#script
#!/bin/bash
greet() {
        read -p "Pleae enter your name:" NAME
        echo "Hello , $NAME"
}

add(){
        read -p "Enter 1st number:" NUM1
        read -p "Enter 2nd number:" NUM2
        sum=$((NUM1+NUM2))
        echo "Sum of both number is :$sum"
}
greet
add

#output
./functions.sh
Pleae enter your name:mansi
Hello , mansi
Enter 1st number:7
Enter 2nd number:3
Sum of both number is :10
```
## Task-2
disk_check.sh
``` bash
#!/bin/bash

check_disk(){
        echo "Disk usage of /"
        echo "------------------------------------------------"
        df -h /
}

check_memory(){
        echo "------------------------------------------------"
        echo "available memory"
        free -h
}
check_disk
check_memory

#output
./disk_check.sh
Disk usage of /
------------------------------------------------
Filesystem      Size  Used Avail Use% Mounted on
/dev/root       8.7G  2.1G  6.6G  24% /
------------------------------------------------
available memory
               total        used        free      shared  buff/cache   available
Mem:           914Mi       360Mi       445Mi       3.0Mi       265Mi       553Mi
Swap:             0B          0B          0B
```
## Task-3
### Set -euo pipefail
- set -euo pipefail is used in shell scripts to make them safer and more reliable.
- It tells the script to stop immediately when something goes wrong, instead of continuing silently.
### What each option does
#### -e (exit on error)
- Stops the script if any command fails.
- Prevents the script from continuing with incorrect results.

#### -u (unset variable check)
- Stops the script if an undefined variable is used.
- Helps catch typing mistakes and missing variables.

#### pipefail (pipeline error handling)
- Fails the script if any command in a pipeline fails, not just the last one.
- Ensures errors inside pipelines are not ignored.
``` bash
#script
#!/bin/bash
set -euo pipefail

echo "Script starting"
ls -l /home/mydirectory
echo "Hello $NAME"
cat hello.txt | echo "This is will not execute"
echo "Script ended"

#output
Script starting
ls: cannot access '/home/mydirectory': No such file or directory
```
## Task-4
``` bash
#!/bin/bash

myfunc() {
    local scope="this is local variable"
    echo "Inside function: $scope"
}

myfunc
echo "----------------------------------------------"
echo "Calling variable outside of the function"

if [[ -z "${scope+x}" ]]; then
    echo "scope is NOT accessible outside the function (not set)"
else
    echo "scope leaked outside: $scope"
fi

#output
./local.sh
Inside function: this is local variable
----------------------------------------------
Calling variable outside of the function
scope is NOT accessible outside the function (not set)
```














