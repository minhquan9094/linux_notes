# Notes for something working on Linux

### 1. Increase /dev/mapper/ubuntu--vg-ubuntu--lv

- Guide:

```
sudo lvextend -l+100%FREE /dev/mapper/ubuntu--vg-ubuntu--lv
sudo resize2fs /dev/mapper/ubuntu--vg-ubuntu--lv
df -h
```

###### Example:

```

quandm@srv-lab-01:~/docker$ sudo lvextend -l+100%FREE /dev/mapper/ubuntu--vg-ubuntu--lv
  Size of logical volume ubuntu-vg/ubuntu-lv changed from <39.00 GiB (9983 extents) to <78.00 GiB (19967 extents).
  Logical volume ubuntu-vg/ubuntu-lv successfully resized.
quandm@srv-lab-01:~/docker$ df -h
Filesystem                         Size  Used Avail Use% Mounted on
tmpfs                              795M  6.0M  790M   1% /run
/dev/mapper/ubuntu--vg-ubuntu--lv   39G   35G  1.2G  97% /
tmpfs                              3.9G     0  3.9G   0% /dev/shm
tmpfs                              5.0M     0  5.0M   0% /run/lock
/dev/sda2                          2.0G  252M  1.6G  14% /boot
tmpfs                              795M  4.0K  795M   1% /run/user/1000
quandm@srv-lab-01:~/docker$ sudo resize2fs /dev/mapper/ubuntu--vg-ubuntu--lv
resize2fs 1.46.5 (30-Dec-2021)
Filesystem at /dev/mapper/ubuntu--vg-ubuntu--lv is mounted on /; on-line resizing required
old_desc_blocks = 5, new_desc_blocks = 10
The filesystem on /dev/mapper/ubuntu--vg-ubuntu--lv is now 20446208 (4k) blocks long.

quandm@srv-lab-01:~/docker$ df -h
Filesystem                         Size  Used Avail Use% Mounted on
tmpfs                              795M  5.9M  790M   1% /run
/dev/mapper/ubuntu--vg-ubuntu--lv   77G   35G   38G  48% /
tmpfs                              3.9G     0  3.9G   0% /dev/shm
tmpfs                              5.0M     0  5.0M   0% /run/lock
/dev/sda2                          2.0G  252M  1.6G  14% /boot
tmpfs                              795M  4.0K  795M   1% /run/user/1000

```
