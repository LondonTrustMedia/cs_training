---
layout: page
title: DNS
display: DNS and Domain Names
order: 4
---
What is DNS, and how does it work? DNS stands for the Domain Name System, and is how your computer converts hostname (such as example.com) into IP addresses (such as 128.46.5.1).


## IP Addresses

Every piece of data that travels through the Internet uses IP addresses. Every machine on the Internet has an IP address, and data is sent between two IP addresses.

However, IP addresses are long and difficult to remember. Here are examples of several IPv4 and IPv6 addresses:

    192.168.23.648
    192.0.2.46
    198.51.100.67
    203.0.113.128

    2001:db8::d7:46e:94a
    fd1e:c93c:4044::94d:e453:2034

These numbers are extremely hard to remember. As well, if the IP address changes, you need to give everyone the new address.


## Names

People don't recognise numbers – people recognise names. A name like `google.com` is easier to remember than `198.51.100.67`.

In addition, even if the IP address changes, you can just point the name to the new IP address. This is why names have stuck around as the primary way to access websites, point to IP space, and access other machines – because of their flexibility and simplicity.


## DNS Servers

How do computers get IP addresses from names using DNS? Computers send the name they have to a DNS server, and the DNS server sends back a matching IP address.

But how does this work, if it means every DNS server needs to store every single name/website on the whole internet? What actually happens is that there are a number of _root_ DNS servers. These servers store essentially every name out there on the internet. If the DNS server you're talking to doesn't know the answer, it asks the root DNS servers and then stores that answer for a while.

Here's a simplified diagram of the DNS:

![DNS]({{ site.baseurl }}/img/articles/networking-dns/dns.svg "DNS")































