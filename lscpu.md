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

Socket(s): 1
Indicates that there is one physical CPU package on the motherboard.

Core(s) per socket: 4
Each CPU package contains 4 physical cores.

Thread(s) per core: 2
Each physical core is capable of running 2 threads concurrently, thanks to hyper-threading.

```
CPU(s) = Sockets × Cores per Socket × Threads per Core
CPU(s) = 1 × 4 × 2 = 8
```

### what is little endian

Byte order (also known as endianness) refers to the order in which bytes are arranged when storing or transmitting multi-byte data (e.g., integers, floating-point numbers) in computer memory.

#### little endian

    store LSB at the lowest memory address followed by increasing memory address

#### Big endian
    store MSB at the lowest memory address followed by increasing memory address

### Address size

Physical Address Size (39 bits physical)
What it is: This specifies the maximum size of physical memory (RAM) that the CPU can directly address.
2 ^ 39 = 549,755,813,888 bytes, or 512 GB.

Virtual Address Size (48 bits virtual)
What it is: This specifies the size of the virtual address space supported by the CPU.
Virtual addresses are used by processes and mapped to physical memory by the OS and the CPU's memory management unit (MMU).
2 ^ 48 =281,474,976,710,656 bytes, or 256 TB.

### NUMA

Non-Uniform Memory Access (NUMA) refers to a memory architecture where the time taken by a processor to access memory depends on whether the memory is local to that processor or located in a different memory region associated with another processor.

- if Numa node is 1 behave similarly as UMA
- due to single socket

### stepping 
The stepping value refers to the revision or update level of a processor's design

### cache
l1 - dedicated to individual cores
  l1d(128 kb) - data
  l1i (128 KB) - instruction

l2 (1 MB)- also dedicated to individual cores

l3 (8 MB)- shared among all cores
