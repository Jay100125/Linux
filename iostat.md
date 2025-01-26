# iostat

- Used for monitor i/o devices
- Can monitor average transfer rate 

```bash
iostat [options] [device] [interval] [count]
```

- Result of `iostat`
```
Device             tps    kB_read/s    kB_wrtn/s    kB_dscd/s    kB_read    kB_wrtn    kB_dscd
loop0             0.00         0.00         0.00         0.00         17          0          0
loop1             0.22        11.62         0.00         0.00     816183          0          0
loop10            0.00         0.00         0.00         0.00        349          0          0
```
| Parameter                            | Description                                                                                         |
|--------------------------------------|-----------------------------------------------------------------------------------------------------|
| Device                               | Name of the storage device                                                                          |
| tps                                  | Transfer rate / sec ( i + o / sec)                                                                  |
| kB_wrtn/s                            | KB written / sec                                                                                    |
| kB_dscd/s                            | KB discarded / sec                                                                                  |
| kB_read                              | Total amount of data read from the device since system started                                      |
| kB_wrtn                              | Total amount of data written from the device since system started                                   |
| kB_dscd                              | Total amount of data discarded from the device since system started                                 |
| %iowait                              | % of CPU time idle while waiting for I/O operations                                                 |
| %irq                                 | % of CPU time spent servicing hardware interrupts                                                   |
| %soft                                | % of CPU time spent servicing software interrupts                                                   |
| %steal                               | % of time CPU waits while hypervisor services another virtual machine                               |
| %guest                               | % of time spent running guest OS in a virtual environment                                           |
| %gnice                               | % of time spent running nice processes on guest OS                                                  |
| %idle                                | % of time CPU was idle                                                                              |



#### -c  

vmspis

CPU stats

```bash
iostat -c
```

Output
```
Linux 5.15.0-130-generic (jay-ThinkPad-T14s-Gen-1)     01/23/2025      _x86_64_        (8 CPU)

avg-cpu:  %user   %nice %system %iowait  %steal   %idle
           4.31    0.01    1.20    0.08    0.00   94.41

```

#### -d

Display devices utilization ( almost same as simple `iostat` command )

```bash
iostat -d
```

#### -x 

Shows extended stats

```bash
iostat -x
```

Output
```
Linux 5.15.0-130-generic (kartikey)     01/23/2025      _x86_64_        (8 CPU)

avg-cpu:  %user   %nice %system %iowait  %steal   %idle
           4.32    0.01    1.20    0.08    0.00   94.40

Device   r/s  rkB/s rrqm/s  %rrqm r_await rareq-sz  w/s  wkB/s wrqm/s  %wrqm w_await wareq-sz  d/s  dkB/s   drqm/s  %drqm d_await dareq-sz  aqu-sz  %util

```

| **Term**       | **Description**                                                                 |
|----------------|---------------------------------------------------------------------------------|
| **Device**     | Name of the storage device (e.g., `sda`, `sdb`).                               |
| **r/s**        | Reads per second (number of read requests per second).                         |
| **rkB/s**      | Kilobytes read per second (amount of data read per second).                    |
| **rrqm/s**     | Read requests merged per second (merged contiguous read requests).             |
| **%rrqm**      | Percentage of read requests merged.                                            |
| **r_await**    | Average read request wait time (in milliseconds).                              |
| **rareq-sz**   | Average read request size (in kilobytes).                                      |
| **w/s**        | Writes per second (number of write requests per second).                       |
| **wkB/s**      | Kilobytes written per second (amount of data written per second).              |
| **wrqm/s**     | Write requests merged per second (merged contiguous write requests).           |
| **%wrqm**      | Percentage of write requests merged.                                           |
| **w_await**    | Average write request wait time (in milliseconds).                             |
| **wareq-sz**   | Average write request size (in kilobytes).                                     |
| **d/s**        | Discards per second (number of discard requests per second).                   |
| **dkB/s**      | Kilobytes discarded per second (amount of data discarded per second).          |
| **drqm/s**     | Discard requests merged per second (merged contiguous discard requests).       |
| **%drqm**      | Percentage of discard requests merged.                                         |
| **d_await**    | Average discard request wait time (in milliseconds).                           |
| **dareq-sz**   | Average discard request size (in kilobytes).                                   |
| **aqu-sz**     | Average queue size (average number of requests in the device queue).           |
| **%util**      | Percentage of time the device was busy (utilization of the device).            |

