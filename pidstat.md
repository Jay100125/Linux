# pidstat
The pidstat command in Linux is used to report statistics about processes.

monitor individual process

```bash
pidstat [options] [interval] [count]
```
### output
``` 
Linux 5.15.0-67-generic (jay-ThinkPad-T14s-Gen-1)       01/26/2025      _x86_64_        (8 CPU)

12:42:47 PM   UID       PID    %usr %system  %guest   %wait    %CPU   CPU  Command
12:42:47 PM     0         1    0.00    0.01    0.00    0.00    0.01     7  systemd
12:42:47 PM     0         2    0.00    0.00    0.00    0.00    0.00     7  kthreadd
12:42:47 PM     0        13    0.00    0.00    0.00    0.00    0.00     0  ksoftirqd/0
12:42:47 PM     0        14    0.02    0.08    0.00    0.03    0.10     4  rcu_sched
12:42:47 PM     0        15    0.00    0.00    0.00    0.00    0.00     0  migration/0
12:42:47 PM     0        21    0.00    0.00    0.00    0.00    0.00     1  migration/1
12:42:47 PM     0        22    0.00    0.00    0.00    0.00    0.00     1  ksoftirqd/1
12:42:47 PM     0        27    0.00    0.00    0.00    0.00    0.00     2  migration/2
```

```bash
pidstat -u # cpu usage
pidstat -r # memory usage
pidstat -d # I/O statistics
pidstat --all # display all info
pidstat -u 1 10 # monitor process over time ( every 1 second for 10 iteration)
pidstat -u -p <pid> 1 # monitor specific process
pidstat -t # monitor threads

