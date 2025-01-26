# ps
The ps command in Linux/Unix is used to display information about active processes. It provides a snapshot of the current running processes, including details like process IDs (PIDs), the user who owns the process, CPU and memory usage, and more.

```bash
ps # running process
ps -e # list all process on the entire system
ps -f # full format listing includes PPID
ps -u # additional info like cpu and memory usage
ps aux # Displays detailed information about all running processes, including memory and CPU usage, and the command that started the process.
ps --forest # Displays processes in a tree structure, illustrating parent-child relationships.
ps -u username # display process of specific username
ps -p <PID> # specific processID
ps -C cmd # specific cmd

```

#### how to find ppid of some pid

```bash
ps -o ppid -p <pid>
```

#### orphan process

```bash
ps -eo pid,ppid,comm | awk '$2 == 1'
```

```bash
ps axms
```

### output
```
 UID     PID          PENDING          BLOCKED          IGNORED           CAUGHT STAT TTY        TIME COMMAND
    0       1 0000000000000000                -                -                - -    ?          0:01 /sbin/init splash
    0       - 0000000000000000 7be3c0fe28014a03 0000000000001000 00000001800004ec Ss   -          0:01 -
    0       2 0000000000000000                -                -                - -    ?          0:00 [kthreadd]
    0       - 0000000000000000 0000000000000000 ffffffffffffffff 0000000000000000 S    -          0:00 -
    0       3 0000000000000000                -                -                - -    ?          0:00 [rcu_gp]
    0       - 0000000000000000 0000000000000000 ffffffffffffffff 0000000000000000 I<   -          0:00 -
    0       4 0000000000000000                -                -                - -    ?          0:00 [rcu_par_gp]
    0       - 0000000000000000 0000000000000000 ffffffffffffffff 0000000000000000 I<   -          0:00 -
    0       5 0000000000000000                -                -                - -    ?          0:00 [slub_flushwq]
    ```

UID: The user ID of the owner of the process.
PID: The Process ID. Represents the unique identifier for a process.
PENDING: A bitmap of pending signals for the process (signals waiting to be delivered).
BLOCKED: A bitmap of signals blocked by the process (signals the process is ignoring).
IGNORED: A bitmap of signals currently being ignored by the process.
CAUGHT: A bitmap of signals currently being caught (handled) by the process.
STAT: The process state:
R: Running.
S: Sleeping (interruptible sleep).
D: Uninterruptible sleep (usually IO-bound).
T: Stopped.
Z: Zombie process.
I<: Idle with low priority (e.g., kernel threads).
Ss: A sleeping process that is also the session leader.
TTY: The controlling terminal associated with the process (if any). A ? indicates no terminal.
TIME: The CPU time consumed by the process.
COMMAND: The name or path of the command that started the process.