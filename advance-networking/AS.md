# Autonomous system
- An Autonomous System (AS) is a collection of interconnected IP networks and routers under the control of a single organization that presents a unified routing policy to the internet.

- communicate other ASes using BGP

- routing inside AS is maintained by interior gateway protocols
- routing between AS is maintained by exterior gateway protocols

### to find your AS
```bash
whois <public-ip> | grep -i 'origin'
```
