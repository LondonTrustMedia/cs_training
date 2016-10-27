---
layout: page
title: IPs and Subnets
order: 5
---
What is a network? A network, in our terms, is a set of computers and other devices, connected via ethernet (internet cables) or wifi, with a consistent set of addresses.

What is a consistent set of addresses, and what really is a network? Let's go over those, and then we can talk about routing.


## IP Addresses

An IP address represents a specific host (device) on a specific network. There are two parts of an IP address – the part which represents the specific network, and the part which represents the specific host. Respectively, these are called the network portion and the host portion.

Let's take a look at some example IP addresses and how they are made up.

---

At home, you probably have a modem which gives you internet access. If you do, you may have seen addresses like this in the past (primarily when configuring your modem):

    192.168.0.x
    192.168.1.x
    10.0.0.x

Where 'x' is 1-255.

Each of these is a separate network. The `192.168.0.x` network contains the addresses `192.168.0.1` to `192.168.0.254`, and the `192.168.1.x` network contains the addresses `192.168.1.1` to `192.168.1.254`.

There are two parts that make up a network – the address, and the subnet mask.


### Subnet Masks

A subnet mask is essentially something that goes over the IP address, to show which parts of it refer to the network, and which parts of it refer to one specific device (or _host_) on the network.

Let's take a look at a simplified example. Let's have an IP address of `5.23.152.22`, and a matching subnet mask of `255.255.255.0`. Here they are, both in decimal and in binary:

    == Decimal ==
     IP address:   5. 23.152. 22
    Subnet mask: 255.255.255.000

    == Binary ==
     IP address: 00000101 00010111 10011000 00010110
    Subnet mask: 11111111 11111111 11111111 00000000








------

-------

-----


## Switching



To really talk about routing, we need to un




What is routing, and what does it let you do?








## Home Routers

## Internet Routing

## What are 'hops'
