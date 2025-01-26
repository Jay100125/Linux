# vmstat
The `vmstat` command in Linux provides detailed information about system performance, including processes, memory, swap, I/O, system, and CPU usage. 

### Command Syntax:
```bash
vmstat [options] [delay] [count]
```
- **`delay`**: The interval (in seconds) between updates.
- **`count`**: The number of times to display the report.

### Output Metrics Breakdown:

#### Procs Metrics
| Metric | Description | Unit |
|--------|-------------|------|
| `r`    | Number of processes waiting for CPU time | Count |
| `b`    | Number of processes in uninterruptible sleep | Count |

#### Memory Metrics
| Metric | Description | Unit |
|--------|-------------|------|
| `swpd` | Amount of virtual memory used | KB |
| `free` | Amount of idle memory | KB |
| `buff` | Memory used as buffers | KB |
| `cache` | Memory used as cache | KB |
| `inact` | Inactive memory (Linux-specific) | KB |
| `active` | Active memory (Linux-specific) | KB |

#### Swap Metrics
| Metric | Description | Unit |
|--------|-------------|------|
| `si`   | Amount of memory swapped in from disk | KB/s |
| `so`   | Amount of memory swapped out to disk | KB/s |

#### IO Metrics
| Metric | Description | Unit |
|--------|-------------|------|
| `bi`   | Blocks received from a block device | KB/s |
| `bo`   | Blocks sent to a block device | KB/s |

#### System Metrics
| Metric | Description | Unit |
|--------|-------------|------|
| `in`   | Number of interrupts, including the clock | Count/sec |
| `cs`   | Number of context switches | Count/sec |

#### CPU Metrics
| Metric | Description | Unit |
|--------|-------------|------|
| `us`   | Time spent on user processes (non-kernel) | Percentage (%) |
| `sy`   | Time spent on system (kernel) processes | Percentage (%) |
| `id`   | Time spent idle | Percentage (%) |
| `wa`   | Time spent waiting for I/O | Percentage (%) |
| `st`   | Time stolen from a virtual machine | Percentage (%) |

### Special Commands:

#### Memory Statistics Since Boot
```bash
vmstat -s
```
This option provides memory-related statistics since the system booted.

#### Disk Information
```bash
vmstat -d
```
This option displays disk-related statistics.

#### Disk Metrics:
| Metric | Description | Unit |
|--------|-------------|------|
| **total** | Total number of read operations completed by the disk | Operations |
| **merged** | Number of adjacent read requests merged into a single request | Requests |
| **sectors** | Total number of sectors read | Sectors |
| **ms** | Total time spent on read operations | Milliseconds |

