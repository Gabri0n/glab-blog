


---
title: "Understanding IPv4 Networking"
date: 2025-04-21
summary: "An overview of IPv4"
tags:
  - "IPv4"
---
# DRAFT, STILL IN PROGRESS
After reading this post you will be able to explain what IPv4 and IPv6 addresses are, how they are created, how they are used, and how they, along with the necessary hardware, run the internet. Happy reading!

## A Brief History
---
January 1st, 1983, the day that ARPANET transitioned from NCP to the new TCP/IP standard setting in motion a system of global connectivity and communication. It allowed for nearly 4.3 billion publicly routable addresses. Its use would continue to grow until January 31, 2011, in which the last remaining IPv4 addresses were allocated from the remaining address pools. From that point onward no more public IPv4 addresses could be handed out and the internet had reached its peak size of 4,294,967,296 public devices with dedicated addresses. 

Fortunately the IETF (Internet Engineering Task Force) saw this coming and in 1998 presented a new standard for TCP/IP addressing called IPv6. This new standard would provide 340 undecillion addresses! That is 3.4 x 10 ^ 38! More than double the estimated amount of grains of sand on the entire planet (10 ^ 18). Not only did it allow for more addresses but it completely removed the need for systems like NAT thus simplifying and speeding up the internet. 

It is now the year of 2025, 14 years after we exhausted the IPv4 address space and yet we still see widespread use of IPv4, both publicly and privately. Even with the larger address space and improvements upon its predecessor google reports only 45% of its traffic comes from IPv6 addresses. While this doesn't account for private use it is still a larger majority of the internet that is on IPv4. That being said, IPv6 is still on the rise. looking back at the same google statistics there has been a 15% increase in the last 5 years alone and it appears to be growing at the same steady rate. 

The truth is that when IPv4 was created in 1983 it was supposed to be like the IPv6 we have now. The internet was much smaller back then. The idea of filling up 4.3 billion addresses was unthinkable especially when the only users of the internet were universities and the military. It was something that was not accessible to the every day person. There was no need for NAT and private address space since there was more than enough addresses to be handed out. The problems only started to occur once the internet became more readily available with more and more business's and organizations requiring public addresses. Some arbitrarily long time in the future we may once again see a new standard assuming we can fill up IPv6's enormous address space. Maybe IPv8 will one day exist!

That's enough history and speculation, lets get into the details!

## The Structure of an IPv4 Address
---
First, lets understand how an IPv4 address is created. IPv4 addresses are created out of 4 one to three digit numbers seperated by a decimal with a max value of 255. Here is an example.

<center>

192.168.1.1

</center>

IP addresses are represented in decimal or base 10 format to make them more readable to humans. Computers operate in binary, 1s and 0s. So, the above address when read by a computer actually looks like this.

<center>

11000000.10101000.00000001.00000001

</center>

Looking at this address you may notice a pattern, each section is exactly 8 digits long. Technically speaking each section is 8 bits long with a bit being either a 1 or 0. These 8 bits form what is called a byte. So overall IP addresses are 4 bytes or 32 bits in size. 

So how does the human readable address represented in decimal/base 10 go to the computer readable address represented in binary/base 2? 

First, lets do a quick review of number systems. In a base 10 system, which is the numbering system we use everyday, there are 10 digits that can be used to represent a value, these digits are 0-9. The value of a number is read based on the position of each digit in columns. For example the number 192 is read as one hundred and ninety two.

<center>

|Hundreds|Tens|Ones|
|:-:|:-:|:-:|
|1|9|2|

</center>

The value of each column is created by calculating 10 to the power of X. So to get the three columns needed to represent 192 we would do 10^0 = 1 (ones), 10^1 = 10 (tens), and 10^2 = 100 (Hundreds).

With these columns we can break down the value of 192. The digit 1 is held in the hundreds column, the digit 9 in the Tens column, and the digit 2 in the Ones column. Thus creating the value 192 or one hundred and ninety two.

Using this knowledge how does this work in binary? In a binary system, also known as base 2, there exists only 2 values being a 1 or a 0. Representing 1 or 0 in binary is very easy as it can just be shown as 1 or 0! Expressing numbers above this though requires some math. In the base 10 system the columns that represent a digits value is expressed as Ones, Tens, Hundreds etc... In a base 2 system however we would use 2 to the power of X to define our columns.
<center>
<table>
  <tr>
    <th>Function</th>
    <td>2^7</td>
    <td>2^6</td>
    <td>2^5</td>
    <td>2^4</td>
    <td>2^3</td>
    <td>2^2</td>
    <td>2^1</td>
    <td>2^0</td>
  </tr>
  <tr>
    <th>Value</th>
    <td>128</td>
    <td>64</td>
    <td>32</td>
    <td>16</td>
    <td>8</td>
    <td>4</td>
    <td>2</td>
    <td>1</td>
  </tr>
</table>
</center>

Now that we have the columns that define our value, lets place the first section of our binary address in the table.

<center>
<table>
  <tr>
    <th>Value</th>
    <td>128</td>
    <td>64</td>
    <td>32</td>
    <td>16</td>
    <td>8</td>
    <td>4</td>
    <td>2</td>
    <td>1</td>
  </tr>
    <tr>
    <th>Binary</th>
    <td>1</td>
    <td>1</td>
    <td>0</td>
    <td>0</td>
    <td>0</td>
    <td>0</td>
    <td>0</td>
    <td>0</td>
  </tr>
</table>
</center>

To calculate the base 10 value, we add up the value of each column that has a 1 in it. For example, in the above table we can see that there is a 1 in the 128 column and a 1 in the 64 column. Adding together 128 + 64 gives us a value of 192! Go ahead and work out the other 3 sections and you should see that:

<center>

11000000.10101000.00000001.00000001 base 2 = 192.168.1.1 base 10

</center>

Now that we can create addresses were good to go right! Well, almost. Were still missing a few concepts.  


## IP Classes and sub-netting 
---
Say a university wants to connect 3 devices to the internet. They would contact IANA (Internet Assigned Numbers Authority) who are responsible for controlling how IP addresses are handed out. The IANA would then assign them 123.123.123.1, 123.123.123.2, and 123.123.123.3 as an example. Now, what if some time in the future the university wants to add more devices or even remove some? Suddenly our nice neat consecutive address numbers are ruined! The next address in line could be 456.456.456.9! and if they chose to remove a device that address would get assigned to someone else. Imagine keeping track of 4.3 billion numbers randomly assigned with no particular pattern. 

In order to maintain some form of order addresses are not handed out singleton but in blocks of multiple. This way when an organization needs some addresses they can be handed a block of a couple hundred consecutive addresses, much easier to track while giving them room to grow or shrink.

Yet, what if one organization only needed 10 addresses and another one needed 1000? We could make every block 10 addresses but then we would need to assign 100 blocks to satisfy the requirement of 1000. On the other hand if we make the blocks 1000 addresses then 990 address will have gone to waste that other people could use. With addresses being a finite resource there needed to be a way to more efficiently use the address space. 

---

In order to ensure IP addresses didnt go to waste IP addresses were first divided into 5 Classes named A to E. Classes D and E are reserved for special cases so we wont focus on those. Classes A to C are the main three classes.



Class A ip addresses reside in the range of 0.0.0.0 to 127.255.255.255
Class B ip addresses reside in the range of 128.0.0.0 to 191.255.255.255
Class C ip addresses reside in the range of 192.0.0.0 to 223.255.255.255



Each of these classes can then be split down further into smaller blocks with a process called sub-netting. Lets start with Class C as an example. Sub-netting allows you to split a block of addresses into further blocks by using a new address called a sub-net mask. Below is an example of a Class C address followed by the Class C sub-net mask.

<center>

192.168.1.1 
 255.255.255.0

</center>

Notice that the subnet mask has the value 255 in the first 3 sections but 0 in the last? Each space containing a number other than 0 (usually 255) is what defines the network address. Since the first 3 spaces contain 255 that means that the network address is 192.168.1.0.


In a network, the network address stays the same. The only value that changes is the space not covered by the subnet mask which is known as the Host address. The host address is what is assigned to each device you want to connect together in your network. You can better visualize it like this, N.N.N.H where N represents what belongs to the network address and H represents what belongs to the host address.

Remember when we mentioned that IP addresses can only have a maximum value of 255? Well since the subnet mask of a Class C network only leaves the last section of the IP for the host address there can only be a maximum of 254 hosts on the network. But wait! 254 does not equal 255! Thats true, all you need to know for now is that .0 is reserved as the network address and .255 is reserved as the broadcast address and cant be used. These terms will be explained later.

Class A and B addresses work the same, the only difference being the IP range and the subnet mask. I've created a table with all the information you need to know.

|Class|Range|Subnet|Network/Host|Amount of Addresses|
|-|-|-|-|-|
|A|0.0.0.0 - 127.255.255.255 | 255.0.0.0| N.H.H.H|16,777,214
|B|128.0.0.0 - 191.255.255.255| 255.255.0.0| N.N.H.H|65,534
|C|192.0.0.0 - 223.255.255.255| 255.255.255.0|N.N.N.H|254

Networks  can also be expressed in CIDR notation. For example, a network with the address 192.168.1.0 with a mask of 255.255.255.0 can be written as 192.168.1.0/24. The number after the slash is derived from the amount of 1s in the binary form of the subnet mask. 255.255.255.0 = 11111111.11111111.11111111.00000000 which is 24 ones.

You should also know that these networks can be broken down even further into smaller sub-networks with a technique called VLSM however that can be an entire post on its own so I wont be covering it here. 

## The Issues of IPv4
here

## Quick Recap
---
What have we learned? 

1. IP addresses are 32 bits/4 bytes in length
2. Made up of four sections of three digits separated by decimals 
3. Each section can range from 0-255 in value
4. There are 5 IP classes A-E. ABC are typically used. DE are special.
5. Can be split into different network sizes using subnetting

This would be a great point to to take a break and internalize the information or go back and re-read anything you're not sure of!

## Sources
---

https://upskilld.com/learn/how-does-ipv4-work/
https://en.wikipedia.org/wiki/IPv4_address_exhaustion
https://prefixx.net/news/ipv4-history
https://www.google.com/intl/en/ipv6/statistics.html#tab=ipv6-adoption
https://www.meridianoutpost.com/resources/articles/IP-classes.php
https://www.networkacademy.io/ccna/ip-subnetting/why-do-we-need-ip-subnetting
