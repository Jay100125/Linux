# top

Display real time information like : CPU usage, memory usage, running processes, system load

```bash 
top [options]
```

**Output**
```
top - 11:07:46 up 19:53,  1 user,  load average: 0.62, 0.69, 0.78
Tasks: 284 total,   1 running, 283 sleeping,   0 stopped,   0 zombie
%Cpu(s):  5.0 us,  1.4 sy,  0.0 ni, 93.5 id,  0.1 wa,  0.0 hi,  0.0 si,  0.0 st
MiB Mem :  15616.5 total,   8382.0 free,   2910.8 used,   4323.7 buff/cache
MiB Swap:   2048.0 total,   2048.0 free,      0.0 used.  11870.8 avail Mem 

    PID USER      PR  NI    VIRT    RES    SHR S  %CPU  %MEM     TIME+ COMMAND                                                        
  18104 kartikey  20   0 1159.6g 340816 108104 S  39.2   2.1   9:14.47 code                                                           
  18088 kartikey  20   0   32.6g 152292 112924 S  11.3   1.0   3:14.21 code                                                           
   1525 kartikey  20   0 4860848 331488 108844 S  10.6   2.1  19:14.17 gnome-she
```

### **System Information**

| **Metric**             | **Description**                                                                 |
|------------------------|-------------------------------------------------------------------------------|
| **Time**               | Current system time.                                                          |
| **Uptime**             | Duration since the system was last started.                                   |
| **Users**              | Number of users currently logged in.                                          |
| **Load Average**       | System load over the last 1, 5, and 15 minutes.                               |

### **Task Information**

| **Metric**             | **Description**                                                                 |
|------------------------|-------------------------------------------------------------------------------|
| **Total Tasks**        | Total number of processes running on the system.                              |
| **Running**            | Number of processes actively running.                                         |
| **Sleeping**           | Number of processes waiting for resources.                                    |
| **Stopped**            | Number of processes that are stopped.                                         |
| **Zombie**             | Number of processes terminated but not yet cleaned up.                       |

### **CPU Usage**

| **Metric**             | **Description**                                                                 |
|------------------------|-------------------------------------------------------------------------------|
| **User (us)**          | Percentage of CPU time spent on user processes.                               |
| **System (sy)**        | Percentage of CPU time spent on kernel processes.                             |
| **Nice (ni)**          | Percentage of CPU time for low-priority processes.                            |
| **Idle (id)**          | Percentage of CPU time when idle.                                             |
| **I/O Wait (wa)**      | Percentage of CPU time waiting for I/O operations.                            |
| **Hardware Interrupts (hi)** | Percentage of CPU time handling hardware interrupts.                   |
| **Software Interrupts (si)** | Percentage of CPU time handling software interrupts.                   |
| **Steal (st)**         | Percentage of CPU time stolen by hypervisor for other VMs.                    |

### **Memory Usage**

| **Metric**             | **Description**                                                                 |
|------------------------|-------------------------------------------------------------------------------|
| **Total Memory**       | Total available physical memory (RAM).                                        |
| **Free Memory**        | Amount of unused memory.                                                      |
| **Used Memory**        | Amount of memory currently in use by processes.                               |
| **Buff/Cache**         | Memory used for buffers and cache.                                            |

### **Swap Usage**

| **Metric**             | **Description**                                                                 |
|------------------------|-------------------------------------------------------------------------------|
| **Total Swap**         | Total available swap space.                                                   |
| **Free Swap**          | Amount of unused swap space.                                                  |
| **Used Swap**          | Amount of swap space currently in use.                                        |
| **Available Memory**   | Total memory available for use (RAM + swap).                                  |

### Process informtion

| **Field**   | **Description**                                                                                   |
|-------------|---------------------------------------------------------------------------------------------------|
| **PID**     | Process ID: A unique identifier for the process.                                                  |
| **USER**    | User who owns the process.                                                                        |
| **PR**      | Priority of the process. Lower values indicate higher priority.                                    |
| **NI**      | Nice value: Determines priority adjustment for the process.                                        |
| **VIRT**    | Virtual memory used by the process, including code, data, and shared libraries.                    |
| **RES**     | Resident memory used: The portion of memory currently in RAM.                                      |
| **SHR**     | Shared memory: Amount of memory shared with other processes.                                       |
| **S**       | Process state: Current state of the process (`S` = sleeping, `R` = running).                       |
| **%CPU**    | CPU usage percentage: How much CPU time the process is consuming.                                  |
| **%MEM**    | Memory usage percentage: Percentage of total physical memory used by the process.                  |
| **TIME+**   | Total CPU time consumed by the process since it started.                                           |
| **COMMAND** | Name or command of the process (e.g., `code` for Visual Studio Code, `gnome-she` for GNOME Shell). |


### Manipulate view of the display

```bash 
top 
```

During monitoring of process which commands do what 

* P => Sort process by CPU usage 
* M => Sort process by memory usage
* N => Sort process by PID
* T => Sort process by running time
* k => kill process ( after pressing k we are prompted to enter PID )
* r => Re-nice process ( after pressing r we are prompted to enter PID and it's new priority )
* u => Display process for specific user 
        ```
        top -u kartikey
        ```

* c => Toggle between command name and full command
* i => Toggle between show idle process or not
* s => Change update interval
* 1 => Toggle between show stats for all individual CPU OR overall CPU usage
* d => Same as s 


```bash
top -n 3
```

Gives update for 3 times then exit

```bash
top -b > logs.txt
```

Redirects output into specified file 


```bash
top -o %CPU %MEM ...
```

Sorts output result 


### How to add or remove col 

```bash
top
```

* Press `f`
* Choose col 
* Press `d` to add/remove that col from display

### How to change unit of memory
```bash
export TOPMEM=M
```

or 

```bash
export TOPMEM=G
```
