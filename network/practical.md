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
### 11.How to check reachability of port of multiple ip/ip ranges?
```bash
nmap -p 22 192.168.1.0/24 --open
```

### 12.How to check the IP address, subnet mask, and default gateway of a network interface?
```bash
ip addr show <interface-name>
```

### 13.How to configure a static IP address on a network interface?
```bash
sudo nano /etc/network/interface
iface wlp0s20f3 inet static
address 10.10.8.2
netmask 255.255.0.0
gateway 10.10.1.1
dns-nameservers 8.8.8.8 8.8.4.4
```

### 14.How to flush the DNS cache on your system?
```bash
sudo systemctl restart systemd-resolved
```

##### to check existing arp table = arp-a or ip neigh show

### 16.How to add a static ARP entry to the ARP table?
```bash
arp -s <IP_ADDRESS> <MAC_ADDRESS>
sudo ip neigh add 192.168.1.100 lladdr AA:BB:CC:DD:EE:FF dev lo
```
Flush ARP Entry:
Remove the outdated entry with sudo ip neigh del <IP> dev <interface>.

# 17.How to check the network statistics (e.g., packets sent/received, errors) for a specific interface?
```bash
ifstat -i <interface-name>
```

# 18.How to check the listening ports and established connections on your system?
```bash
netstat -tuln | head -n 5
```
# 19. How to find the process ID (PID) associated with a specific port?
```bash
sudo netstat -tulnp | head -n 5
```

# 20.How to check the MTU (Maximum Transmission Unit) size of a network interface?
```bash
ifconfig
ip link show <interface-name>
```

# 21. how to configure a network interface to use DHCP?
```bash

```


# 22. How to allow or block traffic on a specific port or from specific host
```bash
sudo ufw deny proto tcp from <ip> to<interface> port 80
```

# 23. How to check the system's network interface DNS servers?
```bash
nmcli dev show | grep DNS
resolvectl status
```

# 24. How to check the system's network interface RX/TX packets?
```bash
ifconfig
```
# 25. query an SNMP agent for system information (e.g., system name, uptime).
```bash
snmpget -v2c -c public <IP> <OID>
snmpbulkwalk -v3 -u jaypatel-snmp -l authPriv -A "jaypatel1" -a SHA -X "jaypatel1" -x AES 10.20.41.113 SNMPv2-MIB::sysName.0
```

# 26. perform a walk operation to retrieve all OIDs from an SNMP agent.
```bash
snmpbulkwalk -v2c -c public 10.20.41.113 .1.3.6.1.2.1.1
```
# 27. How to configure SNMPv3 with authentication and encryption?
```bash
sudo net-snmp-create-v3-user -ro -A "motadata" -a SHA -X "motadata" -x AES jaypatel
- ro = read only
-A = my authentication password
-a sha = encryption protocol
-X = my key for encryption
```

# 28. query an SNMPv3 agent using snmpget and snmpwalk.
```bash
snmpget -v3 -u jaypatel -l authPriv -A "motadata" -a SHA -X "motadata" -x AES 10.20.41.113 1.3.6.1.2.1.25.2.2.0

snmpget -v3 -u jaypatel -l authPriv -A "motadata" -a SHA -X "motadata" -x AES 10.20.41.113 HOST-RESOURCES-MIB::hrMemorySize.0
```

# 29. monitor CPU/Memory/Disk usage using SNMP.
```bash
snmpwalk -v3 -u jaypatel -l authPriv -A "motadata" -a SHA -X "motadata" -x AES 10.20.41.113 HOST-RESOURCES-MIB::hrStorageDescr
snmpwalk -v3 -u jaypatel -l authPriv -A "motadata" -a SHA -X "motadata" -x AES 10.20.41.113 HOST-RESOURCES-MIB::hrStorageSize
snmpwalk -v3 -u jaypatel -l authPriv -A "motadata" -a SHA -X "motadata" -x AES 110.20.41.113 HOST-RESOURCES-MIB::hrStorageUsed
```