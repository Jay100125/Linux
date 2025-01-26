# df

stands for "disk free," and it's used to display information about the available disk space on your file system.

```bash
df -h
```
## output

```
Filesystem      Size  Used Avail Use% Mounted on
udev            7.6G     0  7.6G   0% /dev
tmpfs           1.6G  2.1M  1.6G   1% /run
/dev/nvme0n1p2  234G   16G  206G   7% /
tmpfs           7.7G  274M  7.4G   4% /dev/shm
tmpfs           5.0M  4.0K  5.0M   1% /run/lock
tmpfs           7.7G     0  7.7G   0% /sys/fs/cgroup
/dev/loop0      128K  128K     0 100% /snap/bare/5
/dev/loop1      318M  318M     0 100% /snap/code/181
/dev/loop3       56M   56M     0 100% /snap/core18/2846
/dev/loop2       92M   92M     0 100% /snap/gtk-common-themes/1535
/dev/loop4      517M  517M     0 100% /snap/gnome-42-2204/202
/dev/loop5       46M   46M     0 100% /snap/snap-store/638
/dev/loop6       64M   64M     0 100% /snap/core20/1828
/dev/loop7      347M  347M     0 100% /snap/gnome-3-38-2004/119
/dev/loop9       13M   13M     0 100% /snap/snap-store/1216
/dev/loop8      506M  506M     0 100% /snap/gnome-42-2204/176
/dev/loop11      74M   74M     0 100% /snap/core22/1722
/dev/loop16      50M   50M     0 100% /snap/snapd/18357
/dev/loop12     318M  318M     0 100% /snap/code/180
/dev/loop15      45M   45M     0 100% /snap/snapd/23545
/dev/loop14      64M   64M     0 100% /snap/core20/2434
/dev/loop13     350M  350M     0 100% /snap/gnome-3-38-2004/143
/dev/loop10     257M  257M     0 100% /snap/openjdk/2020
/dev/nvme0n1p1  511M  6.1M  505M   2% /boot/efi
tmpfs           1.6G   40K  1.6G   1% /run/user/1000
```

In this output:

-The Filesystem column shows the name of the mounted file system.

-The Used column shows how much disk space is used.

-The Available column shows how much disk space is still available.

-The Use% column shows the percentage of the disk that is used.

-The Mounted on column shows where the file system is mounted.


```bash
df -i
```

| **Feature**              | **Inodes**                                    | **Blocks**                                     |
|--------------------------|-----------------------------------------------|-----------------------------------------------|
| **Purpose**              | Store metadata about files (attributes)      | Store the actual data of the files            |
| **Contains**             | File type, permissions, size, timestamps, pointers to blocks | Actual file content (text, images, etc.)      |
| **Location**             | Stored in a separate inode table             | Stored in data blocks across the disk         |
| **Size**                 | Typically small, often 128 or 256 bytes       | Typically larger (e.g., 4 KB, 8 KB)           |
| **Number of Entries**    | Fixed at the time of file system creation    | Depends on the size of the disk and block size|
| **Impact on File Creation** | If out of inodes, new files cannot be created, even if there is free space | If out of space, new data cannot be written to files |


