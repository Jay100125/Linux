# nslookup

The nslookup (Name Server Lookup) command is a network utility used to query Domain Name System (DNS) servers to obtain domain name or IP address mapping. 

### Interactive mode
Allows you to query the name servers for information about various hosts and domains, or to print a list of the hosts in a domain.

### Noninteractive mode
Prints the names and requested information for a specified host or a domain

```bash
nslookup google.com
```

#### output
```bash
Server:         127.0.0.53
Address:        127.0.0.53#53

Non-authoritative answer:
Name:   google.com
Address: 142.250.192.78
Name:   google.com
Address: 2404:6800:4009:828::200e
```

- Server - This indicates the DNS server that nslookup is using to resolve the domain.
- Address - 127.0.0.53 is the same local resolver.  #53 means it is using port 53, the standard port for DNS queries.
- Non authorized (recursive DNS resolver) answer means it is from DNS cache and not directly from the authorized name server
- ipv4 and ipv6 address

### Flags
```bash
nslookup 8.8.8.8 # reverse lookup
nslookup google.com 8.8.8.8 # specify dns server
nslookup -type=A google.com # Ipv4
nslookup -type=AA google.com # Ipv4 and Ipv6
nslookup -type=MX google.com # mail exchange server
nslookup -type=NS google.com # name server


```

---

## SOA Record Fields 

| Field        | Value                  | Meaning |
|-------------|------------------------|---------|
| **Origin**  | `ns1.google.com`       | The **primary (authoritative) name server** for `google.com`. This is the first DNS server queried for authoritative responses. |
| **Mail addr** | `dns-admin.google.com` | The **email address** of the administrator responsible for managing the DNS zone. The first dot (`.`) is interpreted as `@`, so this corresponds to `dns-admin@google.com`. |
| **Serial**  | `720506950`             | A **unique serial number** for the zone file. It increases every time the DNS records are updated. Secondary name servers check this number to know if they should fetch updated records. |
| **Refresh** | `900 seconds (15 min)`  | The interval at which **secondary (backup) DNS servers** check with the primary server to see if the records have changed. |
| **Retry**   | `900 seconds (15 min)`  | If a secondary DNS server fails to contact the primary server, it will retry after this interval. |
| **Expire**  | `1800 seconds (30 min)` | If a secondary DNS server cannot contact the primary for this duration, it **stops serving cached records** and treats the zone as **invalid**. |
| **Minimum TTL** | `60 seconds (1 min)` | The **minimum Time-To-Live (TTL)** for negative responses (when a record does not exist). Caching servers should wait at least this time before retrying. |

---

