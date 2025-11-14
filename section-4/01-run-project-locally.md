# Run the project Locally

In this lecture we will use the `docker compose` which is installed as part of `docker`.

Just go to the directory of cloned repo and run `docker compose up`.

Video of the lecture is self explanatory.

## modify the volume of instance to 28 gb
### set the volume to the instance
- sudo apt install cloud-guest-utils
- sudo growpart /dev/xvda 1
- sudo resize2fs /dev/xvda1
- df -h
- lsblk

```
ubuntu@ip-172-31-27-215:~/ultimate-devops-project-demo$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/root       6.8G  4.3G  2.5G  64% /
tmpfs           3.9G     0  3.9G   0% /dev/shm
tmpfs           1.6G  888K  1.6G   1% /run
tmpfs           5.0M     0  5.0M   0% /run/lock
/dev/xvda16     881M   89M  730M  11% /boot
/dev/xvda15     105M  6.2M   99M   6% /boot/efi
tmpfs           794M   12K  794M   1% /run/user/1000
ubuntu@ip-172-31-27-215:~/ultimate-devops-project-demo$ lsblk
NAME     MAJ:MIN RM  SIZE RO TYPE MOUNTPOINTS
loop0      7:0    0 27.6M  1 loop /snap/amazon-ssm-agent/11797
loop1      7:1    0 73.9M  1 loop /snap/core22/2133
loop2      7:2    0 50.8M  1 loop /snap/snapd/25202
loop3      7:3    0 73.9M  1 loop /snap/core22/2139
loop4      7:4    0 50.9M  1 loop /snap/snapd/25577
xvda     202:0    0   28G  0 disk 
├─xvda1  202:1    0    7G  0 part /
├─xvda14 202:14   0    4M  0 part 
├─xvda15 202:15   0  106M  0 part /boot/efi
└─xvda16 259:0    0  913M  0 part /boot
ubuntu@ip-172-31-27-215:~/ultimate-devops-project-demo$ sudo apt install cloud-guest-utils
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
cloud-guest-utils is already the newest version (0.33-1).
cloud-guest-utils set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
ubuntu@ip-172-31-27-215:~/ultimate-devops-project-demo$ sudo growpart /dev/xvda 1
CHANGED: partition=1 start=2099200 old: size=14677983 end=16777182 new: size=56621023 end=58720222
ubuntu@ip-172-31-27-215:~/ultimate-devops-project-demo$ lsblk
NAME     MAJ:MIN RM  SIZE RO TYPE MOUNTPOINTS
loop0      7:0    0 27.6M  1 loop /snap/amazon-ssm-agent/11797
loop1      7:1    0 73.9M  1 loop /snap/core22/2133
loop2      7:2    0 50.8M  1 loop /snap/snapd/25202
loop3      7:3    0 73.9M  1 loop /snap/core22/2139
loop4      7:4    0 50.9M  1 loop /snap/snapd/25577
xvda     202:0    0   28G  0 disk 
├─xvda1  202:1    0   27G  0 part /
├─xvda14 202:14   0    4M  0 part 
├─xvda15 202:15   0  106M  0 part /boot/efi
└─xvda16 259:0    0  913M  0 part /boot
ubuntu@ip-172-31-27-215:~/ultimate-devops-project-demo$ sudo resize2fs /dev/xvda1
resize2fs 1.47.0 (5-Feb-2023)
Filesystem at /dev/xvda1 is mounted on /; on-line resizing required
old_desc_blocks = 1, new_desc_blocks = 4
The filesystem on /dev/xvda1 is now 7077627 (4k) blocks long.

ubuntu@ip-172-31-27-215:~/ultimate-devops-project-demo$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/root        27G  4.5G   22G  18% /
tmpfs           3.9G     0  3.9G   0% /dev/shm
tmpfs           1.6G  904K  1.6G   1% /run
tmpfs           5.0M     0  5.0M   0% /run/lock
/dev/xvda16     881M  155M  665M  19% /boot
/dev/xvda15     105M  6.2M   99M   6% /boot/efi
tmpfs           794M   12K  794M   1% /run/user/1000
ubuntu@ip-172-31-27-215:~/ultimate-devops-project-demo$ 
```
