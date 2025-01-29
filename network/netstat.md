# netstat
netstat (network statistics) is a command-line tool in Linux that displays network connections, routing tables, interface statistics, masquerade connections, and more.

```bash
netstat -a # all connection
netstat -t # all tcp connnection
netstat -u # all udp connection
netstat -l # all listning sockets
netstat -n # numerical address instead dns
netstat -r # routing table
netstat -i # show interface
netstat -s # show network statistics
```

# netstat -r in detail

```bash
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
default         _gateway        0.0.0.0         UG        0 0          0 wlp0s20f3
10.20.40.0      0.0.0.0         255.255.252.0   U         0 0          0 wlp0s20f3
link-local      0.0.0.0         255.255.0.0     U         0 0          0 wlp0s20f3
```

---

### **Field Explanations**

| **Field**       | **Description** |
|----------------|----------------|
| **Destination** | The target network or host IP address that packets should be routed to. `default` represents the default route (for all unknown destinations). |
| **Gateway** | The IP address of the gateway (router) used to forward packets. `0.0.0.0` means there is no gateway (direct connection). `_gateway` is an alias for the default gateway. |
| **Genmask** | The subnet mask that defines which part of the destination address is the network and which part is the host. |
| **Flags** | Various flags that indicate the route type (see below for details). |
| **MSS** | Maximum Segment Size – the largest segment of data the connection can send. Usually `0` (default). |
| **Window** | TCP window size – the amount of data that can be sent before waiting for an acknowledgment. Usually `0` (default). |
| **irtt** | Initial Round Trip Time – the estimated time (in milliseconds) for a packet to reach the destination and return. Usually `0` (default). |
| **Iface** | The network interface through which the route is used (e.g., `wlp0s20f3`, which is your Wi-Fi adapter). |

---

### **Flags Explanation**
| **Flag** | **Meaning** |
|----------|------------|
| **U** | Route is **Up** (active) |
| **G** | Route uses a **Gateway** |
| **H** | Route is for a **Host** (not a network) |
| **R** | Route is **Reinstate**d after a failure |
| **D** | Route was **Dynamically** added |
| **M** | Route was **Modified** |
| **A** | Route is **Installed Automatically** |
| **C** | Route is for a **Directly Connected Network** |

---

## The -n flag in netstat tells it to display numerical IP addresses and port numbers instead of resolving them into hostnames and service names.
Why Use -n?
- Faster Output: Resolving hostnames (DNS lookup) can slow down the command.
- Avoid Errors: If DNS is misconfigured, netstat may take longer or fail to resolve names.
- Clearer Output: Shows exact IP addresses and port numbers instead of translated names.

## netstat -i 
```bash
netstat -i
```

### output
```
Kernel Interface table
Iface      MTU    RX-OK RX-ERR RX-DRP RX-OVR    TX-OK TX-ERR TX-DRP TX-OVR Flg
enp0s31f  1500        0      0      0 0             0      0      0      0 BMU
lo       65536    50405      0      0 0         50405      0      0      0 LRU
wlp0s20f  1500  1468914      0  26705 0        342110      0      0      0 BMRU
```


---

### **Column Breakdown**
| Column | Meaning |
|---------|---------|
| **Iface** | Network interface name (e.g., `lo`, `wlp0s20f3`, `enp0s31f`) |
| **MTU (Maximum Transmission Unit)** | Maximum packet size (in bytes) that the interface can handle |
| **RX-OK** | Number of successfully received packets |
| **RX-ERR** | Number of received packets with errors |
| **RX-DRP** | Number of received packets dropped (buffer full, filtering, etc.) |
| **RX-OVR** | Number of received packets lost due to overflows |
| **TX-OK** | Number of successfully transmitted packets |
| **TX-ERR** | Number of transmission errors |
| **TX-DRP** | Number of transmitted packets dropped |
| **TX-OVR** | Number of transmitted packets lost due to overflows |
| **Flg** | Interface flags (status indicators for the interface) |

---

- **Flags: BMU**  
  - **B** = Broadcast  
  - **M** = Multicast  
  - **U** = Interface is up  
- **This means your wired Ethernet interface is available but inactive**.

- **Flags: LRU**  
  - **L** = Loopback  
  - **R** = Running  
  - **U** = Interface is up  
- **This means local system communication is working fine**.

- **Flags: BMRU**  
  - **B** = Broadcast  
  - **M** = Multicast  
  - **R** = Running  
  - **U** = Interface is up  
- **This means your Wi-Fi is actively being used, but some packets are being dropped.**  


### ESTABLISHED

The connection is fully established, and data can be sent and received.
Example: A successful SSH or HTTP connection.
Seen in: Normal working network connections.
### SYN_SENT

The client has sent a SYN (synchronize) packet to initiate a connection but has not yet received a response.
Seen in: Outbound connections that are trying to establish.
### SYN_RECV

The server has received a SYN request and sent a SYN-ACK but is waiting for the client’s final acknowledgment.
Seen in: Servers handling incoming connection requests.
### LISTEN

The socket is listening for incoming connections.
Seen in: Servers waiting for client requests (e.g., web servers, SSH servers).
### CLOSE_WAIT

The remote side has closed the connection, but the local application hasn't closed it yet.
Seen in: Applications that haven't properly closed their socket.
### TIME_WAIT

The connection is closed, but the system is waiting to ensure all packets have been received before freeing the resources.
Seen in: Properly closed connections, but still temporarily holding resources.
### FIN_WAIT1

The local application has closed the connection and sent a FIN packet, but hasn't received an acknowledgment yet.
Seen in: Connections being closed.
### FIN_WAIT2

The local application has sent a FIN and received an acknowledgment but is still waiting for the remote side to close.
Seen in: Connections waiting for remote closure.
### LAST_ACK

The remote side has sent a FIN, and the local side has sent an acknowledgment but hasn't received confirmation yet.
Seen in: Connections in the final closing phase.
### CLOSING

Both sides have sent a FIN but neither has received a final acknowledgment.
Seen in: Rarely, when both sides attempt to close at the same time.
### CLOSED

The connection is completely closed and no longer active.
Seen in: Completed or terminated connections.