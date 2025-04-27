---
title: "Understanding Basic Networking"
date: 2025-04-21
summary: "An overview of Networking"
tags:
  - "Networking"
---

Before jumping in you may want to check out my other post about IPv4 addressing (Link here) as it will be something you need to know about going forward. 

## Fundamentals

First things first, to understand how computers communicate together on networks we should first go over how they do this at a fundamental level.

## Networking
---

### Basic Connectivity

Lets start with an easy example, say we wanted to network two computers together directly. Two desktops connected through an Ethernet cable.
```goat
+--------------+                   +--------------+
|  Computer A  |-------------------|  Computer B  |
+--------------+                   +--------------+
```
First we would need to decide the IP range we would want. Lets use a Class C network address of 192.168.1.0. This will alot us 254 addresses, definitely overkill but it will work for our example. Since we are only networking two devices directly we would want to statically assign them each an address. A Static address is one that is set on the system itself and doesn't change. We can assign computer A 192.168.1.1/24 and computer B 192.168.1.2/24. Now if computer A wants to reach computer B it would do so by contacting 192.168.1.1.

### Multi-Device Networks
Connecting 2 computers together is easy, but what if we want to have more than 2? Well the same process would apply except instead of connecting each device directly, a device called a switch would be used in between. Switches dont use IP address, rather they use what are called MAC addresses or Media Access Control address. I wont go over them in this post, all you need to know is that these addresses are built into the hardware of networking devices and that switches will keep track of 



Each device would connect to the switch and an IP address would be statically assigned to each.

``` goat

+--------------+         +--------+        +--------------+
|  Computer A  |-------- | Switch |--------|  Computer C  |
+--------------+         +--------+        +--------------+
                             |
                             |
                       +------------+
                       | Computer B |
                       +------------+
```

So far we have been statically assigning IPv4 addresses. This requires going to each device and manually configuring them. In networks with hundreds of device having to manually assign each an IP address would take far to long and be very difficult to manage adding and removing devices. To make assigning addresses easier we use whats called DHCP or Dynamic Host Configuration Protocol. DHCP is a protocol that allows devices on a network to automatically be assigned an IP address from a DHCP server. This is known as a dynamic assignment and allows for devices to easily be added and removed without manual interaction. 

### Inter-network Communication
---
