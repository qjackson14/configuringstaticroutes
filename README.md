<p align="center">

</p>


<h2>Video Demonstration</h2>

- ### [YouTube: Day 11 Configuring Static Routes](https://www.youtube.com/watch?v=A2klArc2zxs)

<h2>Environments and Technologies Used</h2>

- Jeremy's IT Lab Youtube Channel
- Cisco Packet Tracer
  

  
<h2>Operating Systems Used </h2>

- Cisco IOS


<h2>Step-by-Step</h2>

Part 1 — Configure R1
Set Hostname

Access R1 CLI

Enter privileged EXEC mode

enable

Enter global configuration mode

configure terminal

Set hostname

hostname R1
Check Interface Status

Enter interface configuration mode

interface g0/0

Verify interface status

do show ip interface brief

Expected:

IP address: unassigned

Method: unset

Status: administratively down

Configure Interface G0/0
ip address 172.16.255.254 255.255.0.0
speed 1000
duplex full
description ## to SW1 ##
no shutdown
Verify Interface
do show ip interface brief

Expected:

Method: manual

Status: up

Configure Unused Interfaces
interface range g0/1 - 2
description ## not in use ##
Verify and Save Configuration
do show running-config
end
copy running-config startup-config
show startup-config
Part 2 — Configure PCs
PC1

Open PC1 → Config → FastEthernet0

IP Address: 172.16.0.1
Subnet Mask: 255.255.0.0
Default Gateway: 172.16.255.254
PC2
IP Address: 172.16.0.2
Subnet Mask: 255.255.0.0
PC3
IP Address: 172.16.0.3
Subnet Mask: 255.255.0.0
PC4
IP Address: 172.16.0.4
Subnet Mask: 255.255.0.0
Part 3 — Configure SW1
Set Hostname
enable
conf t
hostname SW1
Check Interfaces
do show interfaces status
Configure Uplink Interfaces
G0/1 (Connected to R1)
interface g0/1
speed 1000
duplex full
description ## to R1 ##
G0/2 (Connected to SW2)
interface g0/2
speed 1000
duplex full
description ## to SW2 ##
Configure End-Host Ports
interface range f0/1 - 2
description ## to end hosts ##
Disable Unused Ports
interface range f0/3 - 24
description ## not in use ##
shutdown
Verify and Save
do show interfaces status
end
write memory
show startup-config
Part 4 — Configure SW2
Set Hostname
enable
conf t
hostname SW2
Check Interfaces
do show interfaces status
Configure Uplink Interface
interface g0/1
speed 1000
duplex full
description ## to SW1 ##
Configure End-Host Ports
interface range f0/1 - 2
description ## to end hosts ##
Disable Unused Ports
interface range g0/2, f0/3 - 24
description ## not in use ##
shutdown
Verify and Save
do show interfaces status
end
write
show startup-config
Lab Complete

✔ Router interface configured
✔ Switch uplinks configured
✔ End-host ports labeled
✔ Unused ports disabled
✔ PCs assigned IP addresses
✔ Configurations saved on all devices

✅ If you want, I can also help you turn this into a very professional GitHub lab repo like network engineers use (with sections like Topology, Diagram, Commands, Verification, and Troubleshooting).
