---
title: "Understanding Ipv4 and Ipv6"
date: 2025-04-21
summary: "An overview of IPv4 and IPv6"
tags:
  - "IPv4"
  - "IPv6"
---
#DRAFT, STILL IN PROGRESS

# Understanding Ipv4 and Ipv6
After reading this post you will be able to explain what IPv4 and IPv6 addresses are, how they are created, how they are used, and how they, along with the necessary hardware, run the internet. Happy reading!

## A Brief History

January 1st, 1983, the day that ARPANET transitioned from NCP to the new TCP/IP standard setting in motion a system of global connectivity and communication. It allowed for nearly 4.3 billion publicly routable addresses. Its use would continue to grow until January 31, 2011, in which the last remaining IPv4 addresses were allocated from the remaining address pools. From that point onward no more public IPv4 addresses could be handed out and the internet had reached its peak size of 4,294,967,296 public devices with dedicated addresses. 

Fortunately the IETF (Internet Engineering Task Force) saw this coming and in 1998 presented a new standard for TCP/IP addressing called IPv6. This new standard would provide 340 undecillion addresses! That is 3.4 x 10 ^ 38! More than double the estimated amount of grains of sand on the entire planet (10 ^ 18). Not only did it allow for more addresses but it completely removed the need for systems like NAT thus simplifying and speeding up the internet. 

It is now the year of 2025, 14 years after we exhausted the IPv4 address space and yet we still see widespread use of IPv4, both publicly and privately. Even with the larger address space and improvements upon its predecessor google reports only 45% of its traffic comes from IPv6 addresses. While this doesn't account for private use it is still a larger majority of the internet that is on IPv4. That being said, IPv6 is still on the rise. looking back at the same google statistics there has been a 15% increase in the last 5 years alone and it appears to be growing at the same steady rate. 

The truth is that when IPv4 was created in 1983 it was supposed to be like the IPv6 we have now. The internet was much smaller back then. The idea of filling up 4.3 billion addresses was unthinkable especially when the only users of the internet were universities and the military. It was something that was not accessible to the every day person. There was no need for NAT and private address space since there was more than enough addresses to be handed out. The problems only started to occur once the internet became more readily available with more and more business's and organizations requiring public addresses. Some arbitrarily long time in the future we may once again see a new standard assuming we can fill up IPv6's enormous address space. Maybe IPv8 will one day exist!

That's enough history and speculation, lets get into the details!

## The Structure of an IPv4 Address

First, lets understand how an IPv4 address is created. IPv4 addresses are created out of 4 one to three digit numbers seperated by a decimal with the max value being 255. Here is an example.
<center>
192.168.1.1
</center>

IP addresses are represented in decimal or base 10 format to make them more readable to humans. Computers operate in binary, 1s and 0s. So, the above address when read by a computer actually looks like this.
<center>
11000000.10101000.00000001.00000001.
</center>

Looking at this address you may notice a pattern, each section is exactly 8 digits long. Technically speaking each section is 8 bits long with a bit being either a 1 or 0. These 8 bits form what is called a byte. So overall IP addresses are 4 bytes or 32 bits in size. 

So how does the human readable address represented in decimal/base 10 go to the computer readable address represented in binary/base 2? 

First, lets do a quick review of number systems. In a base 10 system, which is the numbering system we use everyday, there are 10 digits that can be used to represent a value, these digits are 0-9. The value of a number is read based on the position of each digit in columns. For example the number 192 is read as one hundred and ninety two.

<center>

|Hundreds|Tens|Ones
|-|-|-|
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



## How Does IPv4 Work?

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
https://en.wikipedia.org/wiki/IPv4_address_exhaustion
https://prefixx.net/news/ipv4-history
https://www.google.com/intl/en/ipv6/statistics.html#tab=ipv6-adoption


