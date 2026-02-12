# Day 13 – Linux Volume Management (LVM)
### Commads used 
``` bash
lvm
pvcreate device_name
vgcreate vg_grp_name
lvcreate -L size -n _name_ group_name
mkfs.ext4 device_name
lsblk
df -h
```
### What I learned 
- I have learned how to add a volume and attach it to a instance
- I have learned how to mount the disk
- I have learned how to mount a using LVM
- LVM flow :- Disk -> physical Volumne -> Volume group -> logical Volume 
