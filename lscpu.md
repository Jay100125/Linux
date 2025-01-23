# lscpu

The lscpu command in Linux provides detailed information about the CPU architecture, including the number of CPU cores, CPU family, model name, threads, CPU cache sizes, and other hardware-related details.

```
lscpu
```
### Output
```
Architecture:                    x86_64
CPU op-mode(s):                  32-bit, 64-bit
Byte Order:                      Little Endian
Address sizes:                   39 bits physical, 48 bits virtual
CPU(s):                          8
On-line CPU(s) list:             0-7
Thread(s) per core:              2
Core(s) per socket:              4
Socket(s):                       1
NUMA node(s):                    1
Vendor ID:                       GenuineIntel
CPU family:                      6
Model:                           142
Model name:                      Intel(R) Core(TM) i7-10610U CPU @ 1.80GHz
Stepping:                        12
CPU MHz:                         699.443
CPU max MHz:                     4900.0000
CPU min MHz:                     400.0000
BogoMIPS:                        4599.93
Virtualization:                  VT-x
L1d cache:                       128 KiB
L1i cache:                       128 KiB
L2 cache:                        1 MiB
L3 cache:                        8 MiB
NUMA node0 CPU(s):               0-7
```