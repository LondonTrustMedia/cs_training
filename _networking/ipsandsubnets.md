---
layout: page
title: IPs and Subnets
order: 6
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

Let's look at the binary information for now.

Where there's a `1` in the binary subnet mask, this means that the above digit in the IP address is part of the network portion of the address. Similarly, where there's a `0` in the binary subnet mask, the digit above is part of the address of the host.

The more `1`'s there are in the subnet mask, the more separate networks there are, and the fewer individual hosts or machines there are in each of those networks. For instance, for an IP / subnet like this one, there are three bits for host information:

    == Decimal ==
     IP address:   5. 23.152. 22
    Subnet mask: 255.255.255.248

    == Binary ==
     IP address: 00000101 00010111 10011000 00010110
    Subnet mask: 11111111 11111111 11111111 11111000

There are three binary digits available for hosts with this subnet mask. This means that in this network, there are eight individual IP addresses available.

---

Let's go back to that first example and work out exactly what it means. 

    == Decimal ==
     IP address:   5. 23.152. 22
    Subnet mask: 255.255.255.000

    == Binary ==
     IP address: 00000101 00010111 10011000 00010110
    Subnet mask: 11111111 11111111 11111111 00000000

There are eight bits available for host information. This means that there are 256 possible addresses (i.e. from `00000000` to `11111111`, or 0 to 255).

However, the first and last address in every network is treated as a special address. In this example, that's `5.23.152.0` and `5.23.152.255`.

The first address in a network represents what's called the _network address_. This is a special address that represents the IP network as a whole, and is not available for actual clients to use.

The last address in a network represents what's called the _broadcast address_. This address is special in that every packet sent to this address is sent to everyone on the network (or _broadcasted_). As such, it's not available for actual clients to use. 

Taking out those two special addresses, that means there are 254 addresses that can actually be used on the network, from `5.23.152.1` and `5.23.152.254`.

















For the subnet mask, the `1`'s always come at the start. On every network out there, number of 1's in the subnet mask stays the same across the whole network. This is so that every device on that network knows which broadcast and network addresses to use.







------

-------

-----


## Switching



To really talk about routing, we need to un




What is routing, and what does it let you do?








## Home Routers

## Internet Routing

## What are 'hops'
