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

✅ Static Routing – CCNA Notes

🟢 Part 1 — Connected and Local Routes

🔹 What Are Connected and Local Routes

Connected routes are automatically added when an IP address is configured on a router interface.

Local routes provide a route to the router’s own IP address.

Connected routes provide a route to the network connected to the interface.

These routes appear in the routing table automatically.

🔹 Routes Per Interface

Each router interface creates two routes.

One connected route for the network.

One local route for the interface IP address.

Example:

If a router has 2 interfaces configured:

2 connected routes

2 local routes

Total = 4 routes

If a router has 3 interfaces configured:

3 connected routes

3 local routes

Total = 6 routes

🔹 Router Knowledge with Default Routes

Routers automatically know how to reach:

Their own IP addresses

Networks directly connected to their interfaces

Routers do not know how to reach remote networks unless additional routes are configured.

If a router receives a packet for an unknown network:

The router drops the packet.

🟢 Part 2 — Default Gateway

🔹 End Host Communication

End hosts such as PCs can communicate directly with devices in their local network.

Example:

PC1 network:

192.168.1.0/24

PC4 network:

192.168.4.0/24

Devices in the same network communicate directly.

🔹 Sending Traffic Outside the Network

To reach networks outside the local network:

Hosts send packets to their default gateway.

A default gateway is simply the router connected to the local network.

Example:

PC1 configuration:

IP Address

192.168.1.10

Default Gateway

192.168.1.1

PC1 sends packets destined for other networks to R1.

🟢 Part 3 — Default Route

🔹 Default Route Concept

A default route is written as:

0.0.0.0/0

This route matches all IP addresses.

It is considered the least specific route.

🔹 How Default Routes Work

A router uses the default route when:

No more specific route exists in the routing table.

Default routes are commonly used to send traffic toward:

The Internet

Another upstream router.

🟢 Part 4 — Packet Flow Example (PC1 → PC4)

🔹 Layer 3 (IP Layer)

Source IP:

192.168.1.10

Destination IP:

192.168.4.10

These do not change during the packet's journey.

🔹 Layer 2 (Ethernet Frame)

When PC1 sends the packet:

Destination MAC = Default Gateway MAC (R1)

PC1 first learns R1’s MAC address using ARP.

🔹 Packet Processing at Routers

When R1 receives the packet:

The router removes the Layer 2 frame.

The router checks its routing table.

If no matching route exists, the router drops the packet.

🟢 Part 5 — Static Routes

🔹 What Is a Static Route

Static routes are manually configured routes.

They tell the router where to forward packets for specific networks.

🔹 Static Route Command Format

ip route [destination network] [subnet mask] [next hop]

Example:

ip route 192.168.4.0 255.255.255.0 192.168.13.3

Meaning:

To reach network 192.168.4.0/24

Forward packets to 192.168.13.3

🟢 Part 6 — Static Routes Required for Communication

To allow PC1 and PC4 to communicate, routers must know how to reach both networks:

192.168.1.0/24

192.168.4.0/24

This ensures two-way reachability.

Without two-way routes:

PC1 might reach PC4

But PC4 cannot send replies back.

🟢 Part 7 — Static Route Configuration

🔹 R1 Configuration

ip route 192.168.4.0 255.255.255.0 192.168.13.3

This tells R1:

Send traffic for 192.168.4.0/24 to R3.

🔹 R3 Configuration

Route to PC1 network:

ip route 192.168.1.0 255.255.255.0 192.168.13.1

Route to PC4 network:

ip route 192.168.4.0 255.255.255.0 192.168.34.4

🔹 R4 Configuration

ip route 192.168.1.0 255.255.255.0 192.168.34.3

🟢 Part 8 — Testing Connectivity

Use the ping command from PC1.

Example result:

5 packets transmitted

5 packets received

0% packet loss

This confirms:

PC1 can reach PC4

PC4 can send replies to PC1

Two-way communication is successful.

🟢 Part 9 — Packet Travel Through the Network

Packet path:

PC1 → R1 → R3 → R4 → PC4

At each router:

The frame is de-encapsulated

The routing table is checked

The packet is re-encapsulated

🔹 Important Rule

The IP addresses remain the same throughout the journey.

The MAC addresses change at every hop.

🟢 Part 10 — Static Route Using Exit Interface

Instead of specifying a next hop, you can specify the exit interface.

Example:

ip route 192.168.1.0 255.255.255.0 g0/0

This tells the router:

Send packets to 192.168.1.0/24 out G0/0.

🟢 Part 11 — Static Route Using Interface and Next Hop

You can specify both.

Example:

ip route 192.168.4.0 255.255.255.0 g0/1 192.168.24.4

🟢 Part 12 — Default Route Configuration

Command:

ip route 0.0.0.0 0.0.0.0 [next hop]

Example:

ip route 0.0.0.0 0.0.0.0 203.0.113.2

Meaning:

Send all unknown traffic to 203.0.113.2.

🟢 Routing Table Codes

C = Connected route

L = Local route

S = Static route

S* = Candidate default route
