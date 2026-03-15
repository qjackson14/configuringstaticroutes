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

<br>✅ Cisco Router and Switch Interface Configuration Lab</br>

- Network: 172.16.0.0/16

<br>🟢 Part 1 — Configure R1</br>
🔹 Set Hostname

- Access R1 CLI.

- Enter privileged EXEC mode: enable

- Enter global configuration mode: configure terminal

- Set hostname: hostname R1

  -🔹 Check Interface Status

- Enter interface configuration mode: interface g0/0

- Check interface information: do show ip interface brief

- Confirm:

- IP address is unassigned

- Method is unset

- Status is administratively down

-🔹 Configure Interface G0/0

- Assign IP address:
- ip address 172.16.255.254 255.255.0.0

- Set interface speed: speed 1000

- Set duplex mode: duplex full

- Add description: description ## to SW1 ##

- Enable interface: no shutdown

- 🔹 Verify Interface

- Check interface status:
- do show ip interface brief

- Confirm:

- IP address is configured

- Method shows manual

- Status shows up

- 🔹 Configure Unused Interfaces

- Enter interface range:
- interface range g0/1 - 2

- Add description:
- description ## not in use ##

- 🔹 Verify Configuration

- View running configuration:
= do show running-config

-🔹 Save Configuration

- Exit configuration mode: end

- Save configuration:
- copy running-config startup-config

- Verify saved configuration:
- show startup-config

- 🟢 Part 2 — Configure PCs
-🔹 PC1

- Click PC1 → Config → FastEthernet0

- Set IP address: 172.16.0.1

- Confirm subnet mask: 255.255.0.0

- Confirm default gateway: 172.16.255.254

-🔹 PC2

- Click PC2 → Config → FastEthernet0

- Set IP address: 172.16.0.2

- Confirm subnet mask: 255.255.0.0

-🔹 PC3

- Click PC3 → Config → FastEthernet0

- Set IP address: 172.16.0.3

- Confirm subnet mask: 255.255.0.0

- 🔹 PC4

- Click PC4 → Config → FastEthernet0

Set IP address: 172.16.0.4

Confirm subnet mask: 255.255.0.0

🟢 Part 3 — Configure SW1
🔹 Set Hostname

Access SW1 CLI

Enter privileged mode: enable

Enter configuration mode: conf t

Set hostname: hostname SW1

🔹 Check Interface Status

Enter command:
do show interfaces status

🔹 Configure G0/1 (Connected to R1)

Enter interface mode:
interface g0/1

Set speed: speed 1000

Set duplex: duplex full

Add description:
description ## to R1 ##

🔹 Configure G0/2 (Connected to SW2)

Enter interface mode:
interface g0/2

Set speed: speed 1000

Set duplex: duplex full

Add description:
description ## to SW2 ##

🔹 Configure End-Host Ports

Enter interface range:
interface range f0/1 - 2

Add description:
description ## to end hosts ##

🔹 Disable Unused Ports

Enter interface range:
interface range f0/3 - 24

Add description:
description ## not in use ##

Disable interfaces:
shutdown

🔹 Verify and Save

Verify interface configuration:
do show interfaces status

Exit configuration mode: end

Save configuration:
write memory

Verify saved configuration:
show startup-config

🟢 Part 4 — Configure SW2
🔹 Set Hostname

Access SW2 CLI

Enter privileged mode: enable

Enter configuration mode: conf t

Set hostname: hostname SW2

🔹 Check Interface Status

Run command:
do show interfaces status

🔹 Configure Uplink Interface

Enter interface mode:
interface g0/1

Set speed: speed 1000

Set duplex: duplex full

Add description:
description ## to SW1 ##

🔹 Configure End-Host Ports

Enter interface range:
interface range f0/1 - 2

Add description:
description ## to end hosts ##

🔹 Disable Unused Ports

Enter interface range:
interface range g0/2, f0/3 - 24

Add description:
description ## not in use ##

Disable interfaces:
shutdown

🔹 Verify and Save

Verify interfaces:
do show interfaces status

Exit configuration mode: end

Save configuration:
write

Verify configuration:
show startup-config

✅ Lab Complete

Hostnames configured on router and switches

Router interface configured with IP address

Speed and duplex configured on uplinks

Interface descriptions added

Unused interfaces disabled

PCs assigned IP addresses

Configurations saved on all devices
