# du
The du command in Linux stands for Disk Usage. It is used to estimate the file space usage of directories and files in a file system.

Displays disk usage for all subdirectories and files in the current directory.

## flags

```bash
du -ah
```
all files

```bash
du -s # total size of current directory
du -h --max-depth=1 # Limits the depth of subdirectories to display.
du --time # last modification