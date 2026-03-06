# packet-tracer-acl-standard-named-lab

# Cisco Packet Tracer Lab – Standard ACL Named

## Objective
Block PC2 (192.168.1.10) from accessing the server while allowing PC3 (192.168.1.20).

## Network Topology



- **PC1:** 192.168.1.10 /24, GW 192.168.1.1
- **PC2:** 192.168.1.20 /24, GW 192.168.1.1
- **Server:** 192.168.3.10 /24, GW 192.168.3.1
- **Router R1:** 
  - G0/0/0 → Switch1 192.168.1.1 /24
  - G0/0/1 → Switch2 192.168.3.1 /24

## Router Configuration

### Interfaces
interface g0/0/0
ip address 192.168.1.1 255.255.255.0
no shutdown
exit

interface g0/0/1
ip address 192.168.3.1 255.255.255.0
no shutdown
exit


### ACL Named


ip access-list standard BLOCK_PC2
deny host 192.168.1.10
permit any
exit

### Apply ACL


interface g0/0/1
ip access-group BLOCK_PC2 out
exit


## Testing

- PC2 ping 192.168.3.10 → ❌ Blocked
- PC3 ping 192.168.3.10 → ✅ Allowed

## Verification


show access-lists
show running-config


## Author
Sanaa El habib kahloul ( More about me on LinkedIn : https://www.linkedin.com/in/sanaa-el-habib-kahloul/ )
