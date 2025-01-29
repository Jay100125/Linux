### 1.Get ping send packets, received packets, loss percent, min, avg, max latency using ping command.
```bash
fping -c 4 10.20.40.28 | awk 'END {print ""}'
```

### 2.Resolve ip address with the detailed summary of multiple host using fping command
```bash
fping -s -c 4 google.com youtube.com facebook.com | awk 'END {print ""}'
```

### 3.How to check for packets received from specific host and port combined.
```bash
sudo tcpdump host 10.20.41.113 and port 443
```

### 4.How to capture network traffic on a specific interface
```bash
sudo tcpdump -i wlp0s20f3
```

### 5.


###### for checking open port in local computer ss -tuln
### 6.Check weather a port is reachable.
```bash
nc -zv 10.20.40.28 22
telnet 10.20.41.115 22
nmap -p 22 10.20.41.115
```

### 7. How to view & up/down the network interfaces?
```bash
sudo ifconfig <interface-name(lo)> up/down
```

### 8.How to find the port which is being used by process?
```bash
sudo netstat -tulnp
sudo netstat -p
```

### 9.How to add & delete entry in Address Routing Table?
```bash
sudo ip route add <destination_network> via <gateway> dev <interface>
```

### 10.How to view the routes used by current network interface?
```bash
ip route show dev wlp0s20f3
netstat -rn | grep wlp0s20f3
```
