---
layout: page
title: DNS
display: DNS and Domain Names
order: 4
---

**THIS ARTICLE IS HALFWAY THROUGH SERIOUS EDITING AND REWRITING**.

What is DNS, and how does it work? DNS stands for the Domain Name System, and is how your computer converts hostname (such as example.com) into IP addresses (such as 128.46.5.1).


## IP Addresses

Every piece of data that travels through the Internet uses IP addresses. Every machine on the Internet has an IP address, and data is sent between two IP addresses.

However, IP addresses are long and difficult to remember. Here are examples of several IPv4 and IPv6 addresses:

    192.168.23.39
    192.0.2.46
    198.51.100.67
    203.0.113.128

    2001:db8::d7:46e:94a
    fd1e:c93c:4044::94d:e453:2034

These numbers are extremely hard to remember. As well, if the IP address changes, you need to give everyone the new address.


## Names

People don't recognise numbers – people recognise names. A name like `google.com` is easier to remember than `198.51.100.67`.

In addition, even if the IP address changes, the name can stay the same (and it will just point towards the new IP address). This is why names have stuck around as the primary way to access websites, point to IP space, and access other machines – because of their flexibility and simplicity.


## DNS Servers

How do computers get IP addresses from names using DNS? Computers send the name they have to a DNS server, and the DNS server sends back a matching IP address.

There are a number of DNS servers which are called the "root DNS servers". These servers know every name on the internet – or at least how to get the IP address for that name.

If your DNS server doesn't know a name, it asks the root DNS servers and then gives you the answer it gets from the root DNS servers (and stores the answer for a while, so if you ask for that name again it can answer you straight away).

How exactly DNS works goes fairly in-depth (more than most need to know), but essentially:

* There are public DNS servers available for anyone to access, such as Google's DNS servers, and the PIA DNS servers.
* Your ISP also usually provides you with a DNS server you can use.
* Some home modem/routers act as a DNS server.
* Some companies have their own DNS server inside the company, so they can direct a custom name like `internal-resources.example.com` to an internal IP address.

However, the DNS server in your home modem/router usually talks to another public DNS server such as your ISP's DNS servers (rather than the root DNS servers directly).


## Service Info




## Security and Monitoring

Having access to someone's DNS lookups gives you a lot of power. If you can see someone's DNS traffic, you can see when they lookup (and presumably try to access) websites.

Here's an example DNS log:

```
2016-10-20 08:04:24 - IP 192.168.23.648 looked up treating-xyz.medicalsite.com
2016-10-20 08:04:24 - IP 203.0.113.128 looked up politicalsite.org
2016-10-20 08:04:24 - IP 192.168.23.12 looked up badsite.info
```

ISPs generally keep a close eye on what their customers lookup, and store this information to give it to whoever asks.

This is the reason we recommend that people don't use their ISP's DNS servers.









---

But how does this work, if it means every DNS server needs to store every single name/website on the whole internet? What actually happens is that there are a number of _root_ DNS servers. These servers store essentially every name out there on the internet. If the DNS server you're talking to doesn't know the answer, it asks the root DNS servers and then stores that answer for a while.

Here's a simplified diagram of the DNS:

![DNS]({{ site.baseurl }}/img/articles/networking-dns/dns.svg "DNS")

From this diagram, you can see that there can be many DNS servers, everywhere from the local modem/router in your house to your ISP providing one for you, to other publicly available ones. All of these feed from the root DNS servers.
