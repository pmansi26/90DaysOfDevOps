# Day 17 – Shell Scripting: Loops, Arguments & Error Handling
## Task-1
1.for_loop.sh
``` bash
#script
#!/bin/bash
my_list=(apple mango banana orange grape)
for item in "${my_list[@]}"; do
        echo "$item"
done

#output
./for_loop.sh
fruits in the list are:-
apple
mango
banana
orange
grape
```
2.count.sh
``` bash
#script
#!/bin/bash
for i in {1..10};do
        echo "$i"
done
or
#!/bin/bash
for (( i=1; i<=10 ; i++ )); do
        echo "$i"
done

#output
./count.sh
1
2
3
4
5
6
7
8
9
10
```
## Task-2
While loop
``` bash
#script
#!/bin/bash
read -p "Enter a number to make countdown:-" NUM
if [[ $NUM -lt 0 || $NUM -eq 0 ]]; then
        echo "Please enter a valid positive number greater than 0"
        exit 1
fi
i=$NUM
while [ $i -ge 0 ];do
        echo $i
        i=$((i-1))
done
echo "done"

#output
./countdown.sh
Enter a number to make countdown:--5
Please enter a valid positive number greater than 0
./countdown.sh
Enter a number to make countdown:-5
5
4
3
2
1
0
done
./countdown.sh
Enter a number to make countdown:-0
Please enter a valid positive number greater than 0
```
## Task-3
greet.sh
``` bash
#script
#!/bin/bash
echo "Hello $1"
echo "Nice to meet you"

#output
- ./greet.sh mansi
Hello mansi
Nice to meet you
- ./greet.sh mansi pampad
Hello pampad
Nice to meet you
```
args_demo.sh
``` bash
#script
#!/bin/bash
echo "Total number of arguments:- $#"
echo "all arguments :- $@"
echo "0th argumetn of the script :- $0 "

#output
- ./args_demo.sh pampad mansi devops engineer
Total number of arguments:- 4
all arguments :- pampad mansi devops engineer
0th argumetn of the script :- ./args_demo.sh
```
## Task-4
```bash
#script
#!/bin/bash

package_list=(nginx curl wget apache2)
sudo apt-get update -y > /dev/null 2>&1

for item in "${package_list[@]}"; do
    if dpkg -s "$item" > /dev/null 2>&1; then
        echo "$item: already installed (skipping)"
    else
        echo "$item: not installed (installing...)"
        if sudo apt-get install -y "$item" > /dev/null 2>&1; then
            echo "$item: installed successfully"
        else
            echo "$item: installation failed"
        fi
    fi
done

echo "Done."

#output
./install_packages.sh
nginx: already installed (skipping)
curl: already installed (skipping)
wget: already installed (skipping)
apache2: not installed (installing...)
apache2: installed successfully
Done.
```
## Task-5
1.safe_script.sh
``` bash
#script
#!/bin/bash
set -e
mkdir /tmp/devops-test || echo "Directory already exists"
cd /tmp/devops-test
touch test{1..10}.txt
echo "directory and files created successfully"

#output
- ./safe_script.sh
directory and files created successfully
#validation
- /tmp$ ls -l
total 32
drwxrwxr-x 2 ubuntu ubuntu 4096 Feb 13 11:14 devops-test
- cd devops-test/
- ls -l
total 0
-rw-rw-r-- 1 ubuntu ubuntu 0 Feb 13 11:14 test1.txt
-rw-rw-r-- 1 ubuntu ubuntu 0 Feb 13 11:14 test10.txt
-rw-rw-r-- 1 ubuntu ubuntu 0 Feb 13 11:14 test2.txt
-rw-rw-r-- 1 ubuntu ubuntu 0 Feb 13 11:14 test3.txt
-rw-rw-r-- 1 ubuntu ubuntu 0 Feb 13 11:14 test4.txt
-rw-rw-r-- 1 ubuntu ubuntu 0 Feb 13 11:14 test5.txt
-rw-rw-r-- 1 ubuntu ubuntu 0 Feb 13 11:14 test6.txt
-rw-rw-r-- 1 ubuntu ubuntu 0 Feb 13 11:14 test7.txt
-rw-rw-r-- 1 ubuntu ubuntu 0 Feb 13 11:14 test8.txt
-rw-rw-r-- 1 ubuntu ubuntu 0 Feb 13 11:14 test9.txt










