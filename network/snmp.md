# SNMPv3 Configuration and Usage Guide
 
## 1. SNMPv3 Configuration Parameters
 
### Basic User Creation Command
```bash
sudo net-snmp-create-v3-user -ro -A <auth_password> -X <enc_password> -a SHA -x AES snmpv3user
```
 
**Parameter Breakdown:**
- `-ro`: Grants read-only access (vs. `-rw` for read-write)
- `-A <auth_password>`: Sets authentication password (SHA hashed)
- `-X <enc_password>`: Sets encryption password (AES encrypted)
- `-a SHA`: Specifies SHA for authentication
- `-x AES`: Specifies AES for encryption
- `snmpv3user`: Username for SNMPv3 communication
 
**Security Note:**
SNMPv3 implements dual-password security:
- Authentication password verifies user legitimacy
- Encryption password protects data transmission
 
### Configuration File Settings
Location: `/etc/snmp/snmpd.conf`
```bash
rouser snmpv3user auth -V systemview
```
 
**Components:**
- `rouser`: Defines read-only user
- `auth`: Requires authentication
- `-V systemview`: Restricts user to specific OID subset
 
## 2. SNMPv3 Query Commands
 
### Fetch Specific OID (snmpget)
```bash
snmpget -v3 -u snmpv3user -l authPriv -a SHA -A <auth_pass> -x AES -X <enc_pass> <agent_IP> 1.3.6.1.2.1.1.5.0
```
 
**Parameters:**
- `-v3`: SNMP version 3
- `-u snmpv3user`: Username
- `-l authPriv`: Security level
- `-a SHA`: Authentication protocol
- `-x AES`: Encryption protocol
- `-A/-X`: Authentication/encryption passwords
 
**Security Levels:**
- `noAuthNoPriv`: No security
- `authNoPriv`: Authentication only
- `authPriv`: Full security
 
**Example Output:**
```
SNMPv2-MIB::sysName.0 = STRING: ubuntu-server
```
 
### Fetch OID Subtree (snmpwalk)
```bash
snmpwalk -v3 -u snmpv3user -l authPriv -a SHA -A <auth_pass> -x AES -X <enc_pass> <agent_IP> 1.3.6.1.2.1.1
```
 
**Example Output:**
```
SNMPv2-MIB::sysDescr.0 = STRING: Linux ubuntu-server 5.4.0-80-generic
SNMPv2-MIB::sysUpTime.0 = Timeticks: (123456) 0:20:34.56
```
 
## 3. Essential Monitoring OIDs
 
### CPU Usage
- OID: `1.3.6.1.4.1.2021.10.1.3.1` (1-minute load average)
- Example: `UCD-SNMP-MIB::laLoad.1 = STRING: 0.25`
 
### Memory Usage
- OID: `1.3.6.1.4.1.2021.4.5.0` (Total RAM in KB)
- Example: `UCD-SNMP-MIB::memTotalReal.0 = INTEGER: 8048864`
 
### Disk Usage
- OID: `1.3.6.1.4.1.2021.9.1.6.1` (Root partition usage)
- Example: `UCD-SNMP-MIB::dskUsed.1 = INTEGER: 4567890`
 
## 4. SNMPv3 vs v1/v2c Comparison
 
| Feature | SNMPv1/v2c | SNMPv3 |
|---------|------------|---------|
| Security Model | Community strings | User-based security |
| Authentication | None (plaintext) | SHA/MD5 |
| Access Control | Limited | Granular |
 
## 5. Common Interview Questions
 
### Q1: MIB Purpose
MIB maps numeric OIDs to readable names and defines exposed parameters.
 
### Q2: Dual Password System
- Authentication password prevents impersonation
- Encryption password prevents eavesdropping
 
### Q3: AuthPriv Meaning
Indicates both authentication and privacy (encryption) are enabled.
 
### Q4: OID Structure
Example breakdown of 1.3.6.1.2.1.1.5.0:
- 1: ISO
- 3: Org
- 6: DoD
- 1: Internet
- 2: mgmt| Encryption | None | AES/DES |
 
- 1: mib-2
- 1: system
- 5: sysName
- 0: instance
 
### Q5: Snmpwalk vs Snmpget
- `snmpget`: Single OID retrieval
- `snmpwalk`: Full subtree retrieval
 
### Q6: Timeticks
Unit of measurement: 1/100th second
Example: (123456) 0:20:34.56 = 1234.56 seconds
 
## 6. Security Best Practices
 
1. Avoid community strings with SNMPv3
2. Prefer AES-256 over deprecated DES
3. Implement firewall restrictions:
```bash
sudo ufw allow from <manager_IP> to any port 161 proto udp
```
 
## Quick Reference
 
| Term | Definition |
|------|------------|
| OID | Parameter identifier in MIB tree |
| MIB | OID to name mapping database |
| authPriv | Authentication + Encryption |
| sysUpTime | Agent uptime in timeticks |
| SNMPv3 | Secure SNMP with user authentication |