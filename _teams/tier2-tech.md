---
layout: page
title: Tier 2 - Tech
display: Tier 2 Technical Team
order: 3
---
In T2 Tech, we see a lot of things that haven't been encountered before. Things like running the app in new environments, figuring out workarounds to issues that are discovered, and similar.

In addition to the details described in the standard Tier 2 team article, we have a number of more specific roles, responsibilities and issues to keep in mind.


## Our Responsibilities

We have a number of responsibilities as the T2 Tech team, including:

- Helping discover and write up workarounds to issues.
- Responding to customer queries.
- Troubleshooting server issues and other trends.
- Updating install steps if required.

This page goes over how to do some of those things not described in the standard T2 team article.


## How to Troubleshoot Server Issues

Server issues come in a variety of different ways. Sometimes the SOCKS proxy just isn't working, sometimes it's that a specific gateway is having large amounts of packet loss, and other times it can be that a specific port on a gateway isn't working as expected.

Let's go through each of these examples and run through how to approach them.


### Speed Issues or Packet Loss

Typically, speed issues are caused by some form of packet loss or delay on responses from the server.

The first step here is to get a specific affected IP address. By having a single IP (server) that's affected, you can confirm all your tests are consistent and that you're not testing different servers when you do different forms of testing on a server.

An MTR test goes a long way in helping us work out what's going on, and is typically the first thing I try once I have an IP to test. Generally, just running an MTR test directly to the server works out what's going on, but if necessary you can also perform additional tests, such as connecting to the VPN and then running MTR tests to other gateways or to a known site such as ours.

Running an MTR test is pretty standard across all three main operating systems. Basically, you install MTR (either through your package manager or by downloading it from the internet), put in the IP address / hostname, and then run it for at least 100 packets. For more information on how to interpret the results of an MTR test, we've got more information [in this article]({{ site.baseurl }}/tech/networking/mtr.html).


### Specific Ports / VPN Issues

These troubles are more difficult to discover and diagnose. Typically, they require connecting to a server using either our app or a stock OpenVPN connection, and then looking through the relevant log files to see what's going on.

With these troubles, we have more specific VPN troubleshooting tips on the Tech site, but how much you know about OpenVPN in general will be invaluable in helping you work out what's going on.

If you do encounter these sorts of errors, and they're not urgent (not affecting a large number of people and/or doesn't affect the core operation of the VPN), it can also be worth letting the QA team know so they can do more involved testing.









