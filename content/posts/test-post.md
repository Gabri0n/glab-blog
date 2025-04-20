---
title: "My First Post"
date: 2024-01-01
summary: "A short summary of my awesome Post."
tags:
  - "Post"
  - "go"
---
# DRAFT, STILL IN PROGRESS

# Understanding Ipv4 and Ipv6

## A Brief History

January 1st, 1983, the day that ARPANET transitioned from NCP to the new TCP/IP standard setting in motion a system of global connectivity and communication. It allowed for nearly 4.3 billion publicly routable addresses. Its use would continue to grow until January 31, 2011, in which the last remaining IPv4 addresses were allocated from the remaining address pools. From that point onward no more public IPv4 addresses could be handed out and the internet had reached its peak size of 4,294,967,296 public devices with dedicated addresses. 

Fortunately the IETF (Internet Engineering Task Force) saw this coming and in 1998 presented a new standard for TCP/IP addressing called IPv6. This new standard would provide 340 undecillion addresses! That is 3.4 x 10 ^ 38! More than double the estimated amount of grains of sand on the entire planet (10 ^ 18). Not only did it allow for more addresses but it completely removed the need for systems like NAT thus simplifying and speeding up the internet. 

It is now the year of 2025, 14 years after we exhausted the IPv4 address space and yet we still see widespread use of IPv4, both publicly and privately. Even with the larger address space and improvements upon its predecessor google reports only 45% of its traffic comes from IPv6 addresses. While this doesn't account for private use it is still a larger majority of the internet that is on IPv4. That being said, IPv6 is still on the rise. looking back at the same google statistics there has been a 15% increase in the last 5 years alone and it appears to be growing at the same steady rate. 

The truth is that when IPv4 was created in 1983 it was supposed to be like the IPv6 we have now. The internet was much smaller back then. The idea of filling up 4.3 billion addresses was unthinkable especially when the only users of the internet were universities and the military. It was something that was not accessible to the every day person. There was no need for NAT and private address space since there was more than enough addresses to be handed out. The problems only started to occur once the internet became more readily available with more and more business's and organizations requiring public addresses. Some arbitrarily long time in the future we may once again see a new standard assuming we can fill up IPv6's enormous address space. Maybe IPv8 will one day exist!

That's enough history and speculation, lets get into the details!

## How Does IPv4 Work?

First, lets understand how an IPv4 address is created. IPv4 addresses are created out of 4 one to three digit numbers seperated by a decimal with the max value being 255. Here is an example.
<center>
192.168.1.1
</center>



IPv4 operates at the network layer (Layer 3) in the OSI model providing 2 specific features: 
1. Logical Addressing
2. Packet Routing

**Logical Addressing** means the ability to assign IP addresses to devices based on the needs of the network. For example, when the city is building a new sub division of houses they must decide the name of the street and the house numbering scheme to be used. Digitally this allows administrators to create networks designed around specific topological and business needs, assigning addresses as they see fit.

IP addressing is just a digital version of postal addressing. For example, when sending a letter through mail you would specify the mailing address of the recipient and include your address as the sender. The letter is then delivered to the postal office where they decide which route the package should take to get to the specified address. The letter is then sent to the recipient after which they can reply using the sender address you specified. IP addressing provides a way to identify where/who to send the data, and where/who to reply to upon receiving the data

**Packet Routing** would be the post office in the above example. When the letter arrives at the post office they look at the information contained on the envelop which is the address in which the letter is addressed to. Based on this information the post office will move the letter to the necessary bin which will be collected by a delivery truck and then delivered to the recipient. When data is sent on a network, based on the destination address, the data will take the needed path to reach its destination. 

When sending a letter across the world however it may need to travel between multiple post offices and facilities to reach its destination. Digitally the same thing happens, the data is routed across multiple networks each one directing the data as needed for it to reach its destination.

Now that we have a high level understanding of IPv4 lets see how it is utilized.



## The Issues of IPv4
here

## How Does IPv6 Work?
here

## Why IPv6 Adoption Has Been Slow
here

## Sources
here

https://upskilld.com/learn/how-does-ipv4-work/



