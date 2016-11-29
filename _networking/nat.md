---
layout: page
title: NAT
order: 11
---
NAT (or more accurately, PAT) is used to place multiple devices behind a single public IP address. Here, we'll go through the difference between public/private networks and exactly how NAT operates.


## Public vs Private IP Addresses

When connected to the global internet, you need to use unique addresses. That is, addresses which are for you and you alone, across the entire internet. If you don't have a unique IP address, when people send traffic to your address there's no telling whether it'll come to you or to the other person with that address.

These are called public IP addresses, and have these properties:

* That IP is unique across the entire internet.
* If you send a packet with that destination IP from anywhere, it will be delivered to the host with that address.













## History

NATs were created to solve a problem. The problem that the designers of the internet were running into is that they were going to run out of IP addresses. There are only a max of around four billion addresses in IPv4, and a lot of that space is either not able to be used or already given away.

Now that's all well and good when there's one computer per house. However, when almost everyone has a smartphone with them, a laptop and possibly also a desktop computer at home every house can end up using 5-10 IP addresses, if not more. And that's not to discount businesses, where each one can have anywhere from 1-10 IPs as well. Especially with the smartphone revolution, it looked like addresses were going to be gone within a few years.

NATs solve this issue by letting ISPs (internet service providers) service multiple devices behind a single IP address. This means that no matter how many internet-connected devices are inside, each house (and most small-medium businesses) can use only a single public IP address.







## Public vs Private IPs









What does NAT let you do?

How does NAT [PAT] work?
