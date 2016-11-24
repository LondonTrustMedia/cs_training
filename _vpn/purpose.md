---
layout: page
title: Purpose
display: VPN Purposes
order: 1
---
Here, we'll go over some of the reasons that VPNs are used, as well as issues that come up for us and for our users themselves.


## What do VPNs do

VPN services aim to mask the public IP address you connect to the internet with, and instead replace it with a public IP given to you by the VPN service. When you're using a VPN service effectively, someone else that you're connecting to on the internet should not have access to your real IP address – just the IP of the VPN service you're using (that is, the IP of the specific VPN gateway you're connected to).

One term I'm going to be using in this document is **Local Adversary**. I use "local adversaries" to refer to people from your network to your ISP's network that are able to see and/or modify your internet traffic. Local adversaries have the ability to see everything that you're sending onto the internet.

Here's a few examples of local adversaries:

* People inside your home network.
* People on your business network (including I.T. staff and admins).
* Your ISP (since they have the ability to monitor and modify any of your internet traffic).
* People or agencies on your ISP's network.


### Why should I use a VPN service?

When using the internet, there are a number of threats that you can encounter. They can come from different sources, and have all sorts of different impacts. VPN services can help you mitigate some of these threats.

Here are some reasons to use VPN services:

* Avoiding attacks, monitoring, traffic modification and censorship by local adversaries.
* Stopping who you're connecting to from getting your public IP address (this is especially useful in home situations, where your public IP can be associated with your house / details).


## Threats

Both us and our users have threats to face. Here we'll quickly go over some of those.


### Primary threats for our users

The main threats for our users include:

* Being monitored by local adversaries.
* Their traffic being modified before it gets to where it's supposed to.
* The remote end of the connection, or people between them and the endpoint, finding out what their public IP address is.


### Primary threats for us

These are the sorts of things we need to worry about, and can really affect whether people use our service:

* The security of our network or apps being subverted.
* Our gateway IPs being blocked by services.
* Virus and other security detections against our software.
* In general, our users' trust in us eroding. 


## Overview

* VPNs protect users by:
    * Changing their public IP address so the remote end can't get it.
    * Encrypting their traffic so that they can't be monitored and or censored.
