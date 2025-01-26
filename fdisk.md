# fdisk

lists the partition tables for all the disks on the system. It shows details about the partitions, including their device names, sizes, partition types, and file systems.

```bash
sudo fdisk -l /dev/loop0
```

### Output
```
Disk /dev/loop0: 4 KiB, 4096 bytes, 8 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes

```

4 KiB - total size of loop device
4096 - in bytes
consist of 8 sector