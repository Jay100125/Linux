# snmpv2c

```bash
snmpget -v2c -c public 10.20.41.113 1.3.6.1.2.1.1.5.0 #hostname

snmpbulkwalk -v3 -u jaypatel-snmp -l authPriv -A "jaypatel1" -a SHA -X "jaypatel1" -x AES 10.20.41.113 SNMPv2-MIB::sysName.0

snmpget -v3 -u jaypatel -l authPriv -A "motadata" -a SHA -X "motadata" -x AES 10.20.41.113 
```
