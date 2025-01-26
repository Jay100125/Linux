# free


The free command in Linux is used to display information about RAM (primary memory) and swap space usage. It provides details about the total, used, free, and available memory in your system.


```bash
free -h
```
## output
```
              total        used        free      shared  buff/cache   available
Mem:           15Gi       3.2Gi       8.6Gi       919Mi       3.5Gi        10Gi
Swap:         2.0Gi          0B       2.0Gi

```

 ### flags

  - k -- kibi.
  - m -- mebi.
  - g -- gibi
  - h -- human readable
  - t -- total for RAM + SWAP
  - s N, --seconds N   repeat printing every N seconds
  - c N, --count N     repeat printing N times, then exit


  ### swap memory
  - Swap memory is part of the secondary storage (disk or SSD).
  - It can be a dedicated partition or a file on the filesystem.
  - While swap helps manage memory overflow, using it extensively can degrade performance due to slower disk access compared to RAM.

  ### free memory
  - Represents the amount of memory completely unused at the moment.
  - This memory is not allocated for any purpose, such as applications, buffers, or cache.
  - Memory that is entirely unallocated

  ### available memory 
   - Represents an estimate of how much memory is available for new processes and applications without swapping.
   - Includes both unused memory (free) and memory currently used by buffers and cache, which the system can reclaim when needed.

  ### shared memory
  - The memory used by tmpfs (temporary file systems) or shared between processes for inter-process communication.
  
  ### buff/cache memory
  **Buffers** :
- Temporary storage for data during I/O operations (e.g., when writing to or reading from a disk).
- Helps manage and optimize I/O operations by reducing frequent disk access.

**cache** :
- Recently accessed data or files stored in memory for faster access.
- Prevents the need to fetch data repeatedly from a slower disk.
- Includes file system cache and data cache.
