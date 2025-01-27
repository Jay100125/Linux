### 1. Get the number of context switches
```bash
vmstat | awk 'NR==3{ print "context switches:"  $12}'
echo "Context switch: $(cat /proc/stat | grep ctxt)"
```

### 2. Get the number of running processes:
```bash
echo "Current running processes are: $(ps | wc -l)"
or for some specific processes
ps -A | grep -c chrome

	ps -Al | awk '{if($2 == "R") count++ } END {print count}'
```

### 3. Get the CPU used and idle percent
```bash
mpstat | awk 'NR == 4 {print "Idle : " $14;  print "Used : " 100-$14}'
```
    
### 4. Get inet address and MAC address
```bash
ifconfig | awk '{if(NR == 19) print "Ip address : " $2; if(NR==21) print "Mac Address: " $2}'
```

### 5. Get context switches per second
```bash
vmstat 1
```

### 6. Get load avg for 1min, 5min and 15min
```bash
uptime | awk '{print "Load Average:"; print "1Min :" $10; print "5Min : " $11; print "15Min : " $12}'
```

### 7. Watch any file for continues modification
```bash
tail -f filename
```

### 8. Get used and free memory
```bash
free -h | grep "Mem" | awk '{printf "Used: %s\nfree : %s\nTotal: %s\n", $3, $4, $2}'
```

### 9. Get used cpu and context switches per process
```bash
pidstat -u
pidstat -w
```

### 10. Get Disk read write stats
```bash
iostat -x | grep "nvme0n1" | awk '{print "Disk : " $1, "\nread/sec : " $2 "\nwrite/sec : " $8, "\nreadbyte: " $2*1024 "\nwriteByte : " $8*1024, "\nUtilization :" $21}'
```

### 11. TCP and UDP connections
```bash
netstat -s | awk '{if(NR >= 31 && NR <= 49) print }'
```

### 12. Running Threads
```bash
pidstat -t
```

### 13. Running processes
```bash
ps -eLf
```

### 14. List all details of file permission, owner, group
```bash
ls -l
```  

### 15. List File stats file type, block size, time of last data modification, time of last status change
```bash
stat --format="Type: %F/Block Size: %o/ Modify: %Y/ Change: %Z" test.java
```

### 16. Maximum number of threads supported by OS Kernel
```bash
cat /proc/sys/kernel/threads-max
```

### 17. List name of zombie processes & interrupted processes
```bash
ps aux | awk '$8 ~ /I/ {print $11}'
ps aux | awk '$8 ~ /Z/ {print $11}'
```
### 18. List All device drives available in my system & exclude loop devices from it
```bash
iostat -d | grep -v "loop"	
```
 
 ### 19. List all partitions & print sector wise details of each partition
 ```bash
sudo fdisk -l
```

### 20. List the size occupied by each directory & size occupied by files inside that directory (separate commands for directory & file)
```bash
df -h |grep -v "loop"
```