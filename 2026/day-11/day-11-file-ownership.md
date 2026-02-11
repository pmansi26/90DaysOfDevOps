# Day 11 – File Ownership Challenge (chown & chgrp)
## Task 1
``` bash
-r--r--r-- 1 ubuntu ubuntu    0 Feb 11 09:19 devops.txt
-rw-r----- 1 ubuntu ubuntu   37 Feb 11 09:20 notes.txt
drwxr-xr-x 2 ubuntu ubuntu 4096 Feb 11 09:24 project
-rwxrwxr-x 1 ubuntu ubuntu   20 Feb 11 09:20 script.sh
```
These are the files of my home directory , Owner :- ubuntu ; Group :- ubuntu
### Difference between Owner and Group
|   Owner      |   Group             |
|---------------|--------------------|
|Single user who owns the filel | Collection of users sharing acces |
|User who creates the file | Creator's primary group|
| Personal control of the file | Shared access for a team| 

## Files & Directories Created
.
├── bank-heist
│   ├── access-codes.txt
│   ├── blueprints.pdf
│   └── escape-plan.txt
├── devops.txt
├── heist-project
│   ├── plans
│   │   └── strategy.conf
│   └── vault
│       └── gold.txt
├── notes.txt
├── project
├── project-config.yaml
├── script.sh
└── team-notes.txt

## Ownership Changes
- devops-file.txt: user:group → berlin:ubuntu
- team-notes.txt : user:group → ubuntu:heist-team
- project-config.yam : user:group → professor : heist-team
- heist-project/ : user:group → professor: planners
- access-codes.txt : user:group → tokyo : vault-team
- blueprints.txt : usre:group → berlin : tech-team
- escape-plan.txt : user:group → nairobi : vault-team 

## Commands Used
``` bash
 31  useradd -m tokyo
   32  sudo useradd tokyo
   33  sudo userdel tokyo
   34  cat /etc/passwd
   35  sudo useradd -m tokyo
   36  cd /home
   37  ls
   38  cd
   39  ls -l
   40  sudo chown tokyo devops.txt
   41  ls -l
   42  sudo useradd -m berlin
   43  cd /home
   44  ls
   45  cd
   46  sudo chown berlin devops.txt
   47  ls -l
   48  touch team-notes.txt
   49  ls -l
   50  sudo groupadd heist-team
   51  cat etc/groups | tail -n 5
   52  cat etc/group | tail -n 5
   53  cat etc/passwd | tail -n 5
   54  cat etc/passwd
   55  cat /etc/groups
   56  cat /etc/group
   57  ls -l
   58  sudo chgrp heist-team team-notes.txt
   59  ls -l
   60  touch project-config.yaml
   61  ls -l
   62  sudo useradd -m professor
   63  man chown
   64  sudo chown project-config.yam professor heist-team
   65  sudo chown professor heist-team project-config.yaml
   66  sudo chown professor -g heist-team project-config.yaml
   67  sudo chown professor:heist-team project-config.yaml
   68  ls -l
   69  mkdir -p heist-project/vault
   70  mkdir -p heist-project/plans
   71  ls -l
   72  mkdir -p heist-project/vault
   73  mkdir -p heist-project/plans
   74  touch heist-project/vault/gold.txt
   75  touch heist-project/plans/strategy.conf
   76  ls -l
   77  cd heist-project
   78  ls
   79  cd plans
   80  ls
   81  cd ..
   82  cd vault
   83  ls
   84  cd
   85  sudo groupadd planners
   86  sudo chown -R professor:planners heist-project/
   87  ls -lR heist-project/
   88  sudo useradd -m nairobi
   89  sudo groupadd vault-team
   90  sudo groupadd tech-team
   91  cat /etc/groups
   92  cat /etc/group | tail -n 5
   93  touch bank-heist/access-codes.txt
   94  touch bank-heist/blueprints.pdf
   95  touch bank-heist/escape-plan.txt
   96  ls -l
   97  mkdir bank-heist/
   98  touch bank-heist/access-codes.txt
   99  touch bank-heist/blueprints.pdf
  100  touch bank-heist/escape-plan.txt
  101  ls -l
  102  cd bank-heist
  103  ls -l
  104  sudo chown tokyo:vault-team access-codes.txt
  105  sudo chown berlin:tech-team blueprints.pdf
  106  sudo chown nairobi:vault-team escape-plan.txt
  107  ls -l
```

## What I Learned
- I learned how to change user and group of complete directory using -R 
- #sudo chown -R professor:planners heist-project/
- Got confidence on chown , chgrp commands 

