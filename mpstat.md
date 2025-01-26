# mpstat
The `mpstat` command in Linux is a part of the **sysstat** package and is used for reporting CPU statistics. It provides information about CPU usage on a per-processor basis (useful for multi-core systems) and helps monitor the performance and load of individual CPU cores.

### **Basic Syntax:**

```bash
mpstat [options] [interval] [count]
```

- **`options`**: Various flags that specify what information to display.
- **`interval`**: The interval in seconds between each report. For example, `1` means the data will be reported every 1 second.
- **`count`**: The number of times the statistics will be reported.

### **Commonly Used Options in `mpstat`:**

1. **`-P`**: Display stats for a specific CPU (e.g., `-P ALL` for all CPUs).
2. **`-u`**: Show only the user-level CPU utilization (this is the default).
3. **`-I`**: Display interrupt statistics.
4. **`-w`**: Display statistics in a more human-readable way (more detailed info).

### **Understanding the Output of `mpstat`:**

By default, `mpstat` shows the **CPU usage stats**. Here's what the output means:

```bash
mpstat 1 5
```

Output example:

```
Linux 5.4.0-42-generic (hostname)  01/23/2025  _x86_64_    (4 CPU)

Average:    CPU    %usr   %nice    %sys   %iowait    %irq   %soft   %steal   %guest  %gnice   %idle
Average:   all   10.27    0.00    3.15     2.13     0.01     0.09     0.00     0.00     0.00    84.35
```

### **Key Columns:**
- **`CPU`**: The ID of the CPU. "all" represents the combined usage of all CPUs.
- **`%usr`**: Percentage of CPU time spent in user space (non-kernel code).
- **`%nice`**: Percentage of CPU time spent on processes with a positive nice value (lower priority).
- **`%sys`**: Percentage of CPU time spent in the kernel space (system processes).
- **`%iowait`**: Percentage of CPU time waiting for I/O operations (disk, network, etc.).
- **`%irq`**: Percentage of CPU time spent handling hardware interrupts.
- **`%soft`**: Percentage of CPU time spent handling software interrupts.
- **`%steal`**: Percentage of time a virtual CPU waits for the real CPU while the hypervisor is servicing another virtual processor (relevant for virtualized environments).
- **`%guest`**: Percentage of CPU time spent running a virtual machine.
- **`%gnice`**: Percentage of CPU time spent on processes with a negative nice value.
- **`%idle`**: Percentage of CPU time that is idle and not doing any work.

### **Example 1: Display CPU statistics for all processors every 1 second, 5 times**

```bash
mpstat -P ALL 1 5
```

Output:

```
Linux 5.4.0-42-generic (hostname)  01/23/2025  _x86_64_    (4 CPU)

Average:    CPU    %usr   %nice   %sys   %iowait   %irq   %soft   %steal   %guest  %gnice   %idle
Average:   all    10.27    0.00    3.15     2.13    0.01    0.09    0.00    0.00    0.00    84.35
Average:      0    15.27    0.00    4.12     3.05    0.00    0.00    0.00    0.00    0.00    77.56
Average:      1    12.00    0.00    2.00     2.50    0.00    0.00    0.00    0.00    0.00    83.50
Average:      2    8.00     0.00    3.50     2.00    0.00    0.00    0.00    0.00    0.00    86.50
Average:      3    9.00     0.00    3.00     1.00    0.00    0.00    0.00    0.00    0.00    87.00
```

This example shows the CPU statistics for **all CPUs** (with `-P ALL`) every **1 second** for **5 intervals**.

### **Example 2: Display statistics for a single CPU (CPU 0)**

```bash
mpstat -P 0 1 5
```

Output example:

```
Linux 5.4.0-42-generic (hostname)  01/23/2025  _x86_64_    (4 CPU)

Average:    CPU    %usr   %nice   %sys   %iowait   %irq   %soft   %steal   %guest  %gnice   %idle
Average:      0    12.27    0.00    3.00     1.50    0.00    0.00    0.00    0.00    0.00    83.23
```

This command will display the CPU statistics for **CPU 0** only.

### **Example 3: Display only user CPU time (with `-u` option)**

```bash
mpstat -u 1 5
```

This will output only the **user CPU time** (`%usr`) for the specified interval, providing a focus on how much of the CPU is being used by user applications.

### **Real-World Use Cases for `mpstat`:**

1. **Monitoring CPU Load:**
   - Use `mpstat` in a script to monitor CPU utilization over time and track performance, especially during high load or while troubleshooting performance issues.
   
2. **Identifying CPU Bottlenecks:**
   - By checking individual CPU stats (with `-P`), you can identify whether certain CPUs are under heavy load while others remain idle, which may indicate uneven workload distribution.

3. **Virtualization Performance:**
   - In virtualized environments, the **steal time** (`%steal`) in `mpstat` can help identify performance issues caused by the hypervisor taking CPU cycles away from virtual machines.

4. **CPU Bound Processes:**
   - Use `mpstat` in combination with `ps` or `top` to identify which processes are consuming the most CPU resources over time.
