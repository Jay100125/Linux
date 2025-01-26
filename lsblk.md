# lsblk
The lsblk command in Linux is used to list information about all available or specified block devices on the system, such as hard drives, SSDs, partitions, and other storage devices. It shows the structure and hierarchy of block devices, which is especially useful for viewing devices and partitions in a tree-like format.
Basic Syntax:
```
lsblk [options]
```
Commonly Used Options with lsblk:

    -a:
        Show all devices, including empty devices that do not contain any partitions.
        Example: lsblk -a

    -f:
        Show the filesystems, UUIDs, labels, and other filesystem-related information for each block device.
        Example: lsblk -f

    -l:
        Display the block devices in a list format, rather than the default tree format.
        Example: lsblk -l

    -o <columns>:
        Customize the output by specifying which columns to display.
        Example: lsblk -o NAME,SIZE,TYPE,MOUNTPOINT

    -d:
        Show only the disk devices, excluding partitions or other types of block devices.
        Example: lsblk -d

    -n:
        Avoid printing the header row (useful for parsing the output).
        Example: lsblk -n

    -r:
        Show raw device names (useful for parsing).
        Example: lsblk -r

    -p:
        Show the full path of the devices (e.g., /dev/sda instead of sda).
        Example: lsblk -p

    -x:
        Show the output in a comma-separated format (good for CSV-like output).
        Example: lsblk -x

Basic Output Explanation of lsblk:

Here's an example output of the lsblk command:

lsblk

Output:
```
NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sda      8:0    0   100G  0 disk
├─sda1   8:1    0    50G  0 part /mnt/data
├─sda2   8:2    0    50G  0 part /mnt/backup
sdb      8:16   0   200G  0 disk
├─sdb1   8:17   0   100G  0 part /mnt/storage
└─sdb2   8:18   0   100G  0 part /mnt/extra
```
Explanation of the Columns:

    NAME: The name of the device (e.g., sda, sda1, sdb).
    MAJ:MIN: Major and minor device numbers (used internally by the kernel).
    RM: Whether the device is removable (1 for yes, 0 for no).
    SIZE: The size of the device or partition.
    RO: Whether the device is read-only (1 for yes, 0 for no).
    TYPE: The type of device (e.g., disk, part for partition).
    MOUNTPOINT: The mount point for the device or partition, if it is mounted. If it's not mounted, this will be empty.


### Loop device

A loop device in Linux is a pseudo-device that allows a file to be treated as a block device. Essentially, it enables you to mount a file (such as an ISO image or a disk image) as if it were a physical disk or partition.

#### don't want to show loop device

```
 lsblk -e 7
```