# Day 16 – Shell Scripting Basics
## Task-1 
#### What happens if you remove the shebang line?
- If you remove the shebang line, the OS doesn’t know which interpreter to use.
- Running the script as ./script may fail or run incorrectly.
- Running it with an explicit interpreter (bash script, python3 script.py) still works.
- It can cause the script to run with the wrong shell/interpreter, leading to errors.
#### Script
``` bash
#script
#!/bin/bash
echo "Hello , Devops !"

#output
ubuntu@ip-172-31-74-20:~$ ./hello.sh
Hello , Devops !
```
## Task-2
#### Try using single quotes vs double quotes — what's the difference?
If I use single quotes instead of double quotes the variables wont work and they wont expand it will print exact literal text 
#### Script
``` bash
#script
#!/bin/bash
NAME="Mansi"
ROLE="Devops Engineer"
echo "Hello , I am $NAME and I am a $ROLE"

#output
ubuntu@ip-172-31-74-20:~$ ubuntu@ip-172-31-74-20:~$ ./variables.sh
Hello , I am Mansi and I am a Devops Engineer
```
## Task-3
#### Script
``` bash
#!/bin/bash
read -p "What is your name " NAME
read -p "What is your favorite tool " TOOL
echo "Hello $NAME , your favorite tool is $TOOL"

#output
ubuntu@ip-172-31-74-20:~$ ./greet.sh
What is your name mansi
What is your favorite tool kubernetes
Hello mansi , your favorite tool is kubernetes
```
## Task-4
#### Script
#### Checking numbers 
``` bash
#!/bin/bash

read -p "Enter a number : " NUM
if [ $NUM -lt 0 ]; then
        echo "$NUM is a negative number"
elif [ $NUM -gt 0 ]; then
        echo "$NUM is a positive number"
else
        echo "$NUM is equal to 0"
fi

#output
./check_numbers.sh
Enter a number : 26
26 is a positive number
./check_numbers.sh
Enter a number : -88
-88 is a negative number
./check_numbers.sh
Enter a number : 0
0 is equal to 0
```
#### Checking file 
``` bash
#!/bin/bash

read -p "Enter a file to check : " FILE
if [ -f "$FILE" ];then
        echo "file exists"
else
        echo "file does'nt exists"
fi

#Output
./file_check.sh
Enter a file to check : hello.sh
file exists
./file_check.sh
Enter a file to check : script.sh
file exists
./file_check.sh
Enter a file to check : hello.txt
file does'nt exists
```
## Task-5

