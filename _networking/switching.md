---
layout: page
title: Switching
order: 7
---
Simply put, switching is what happens inside of a network. Whenever packets are exchanged between two devices on the same network, they are exchanged using switching. When packets are exchanged between devices on different networks, it's called routing (but we won't deal with that here).


## Special Devices

There are several special devices inside of a network. Here's a diagram, and we'll go through what each of these devices does:

![Network]({{ site.baseurl }}/img/articles/networking-switching/network.svg "Network")


### Hub / Switch

Network device which takes incoming packets from one port, and puts them out the appropriate ports to reach their destination.


### Gateway

Simply put, the _gateway_ is the device which can talk to places that are outside this network. In other words, if a computer wants to send a packet to an IP address that isn't on the same network, it'll send it to the gateway instead (and the gateway will send it where it needs to go from there).


### DNS Server

Simply put, the DNS server translates names (such as `google.com`) into IP addresses (such as `203.0.113.128`). In IP, there's nothing but IP addresses. So before sending a packet to something like `google.com`, your computer contacts the DNS server to retrieve the IP address for that name.

If you need a refresher here, feel free to view the DNS page where this system is explained in more detail.


### DHCP Server

We'll go over this in more detail, but put simply:

* Every device on the network needs to be able to get an IP address once they plug into the network.
* Every device needs to know which gateway and DNS server to use while connected to the network.

The DHCP server does this by telling new computers which IP address they can use, and the addresses of the DNS server and the gateway.

Commonly, a number of these roles will be fulfilled by a single device. For instance, most home modem/routers that ISPs provide act as a switch, a gateway, and a DHCP server (pointing computers on the network to use the ISP's DNS servers).

Now that we've gone through each of the standard roles in a network, let's go into more detail about how each of them works.


## Switching

Within a network, devices have two addresses:

* IP address.
* Hardware address.

The IP address changes every time that the device is plugged into a new network. However, the _hardware address_ always stays the same. Because of this, the hardware address stays the same before the device gets an IP address, while it's negotiating one, and after it's gotten an IP address. Having a single, static address vastly simplifies things for the other devices on the network.

This is very useful, because within networks, this hardware (or _Ethernet_) address is how computers direct traffic towards each other, and towards the gateway.

The normal name used for this hardware address is a MAC address. In other words, on typical network, devices have both a static MAC address (that does not change), and an IP address (that can change).

<div class="advanced">
	<p><strong>MAC addresses</strong></p>
    <p>A MAC address is represented by 12 hexidecimal digits, usually split into groups of two. For example, something like `af:42:7b:c3:d4:19`</p>
    <p>In the examples here we'll be using a shortened 4-digit version, both to simplify our diagrams and prevent the explanations from getting bogged-down.</p>
</div>

Now let's talk about how packets get exchanged within a network.

Devices send packets through a hub or a switch with the appropriate MAC/IP addresses, and those devices forward the packets onto their destination.

In terms of physical network ports, hubs and switches are exactly the same. Here's the diagram of a hub/switch:

![Hub / Switch]({{ site.baseurl }}/img/articles/networking-switching/hub-switch.svg "Hub / Switch")

### Hubs

Hubs are essentially the older, simplified cousin of switches. They are simpler to explain, so we'll start with them.

Hubs act on incoming packets. Whenever a hub receives an incoming packet on one port, that packet is send out to every other port. For instance:

![Hub Packet Forwarding]({{ site.baseurl }}/img/articles/networking-switching/hub-packet.svg "Hub Packet Forwarding")

Any devices that get a packet not addressed to them simply drop it without processing it. In this way, hubs deliver packets to their destination within a network.

Essentially, every packet sent through a hub is treated as a broadcast (i.e. it's sent to every device on the network). This does work, and did work fine for a number of years. However, once you get enough computers connected to a network of hubs, performace can be greatly impacted.

Let's take a look at an example network of hubs, and how a packet from Computer A to Computer B gets sent through the network:

![Hub Network]({{ site.baseurl }}/img/articles/networking-switching/hub-network.svg "Hub Network")

The packet from Computer A is sent to every single hub and every single computer on the network. Computer E correctly receives the message, but so does everyone else on the network as well. When every computer starts packets thousands of times a second across the network, errors start happening.

Let's say that Computer D and Computer F send packets one after each other. What ends up happening is that in the middle, the hubs receive both packets at the same time. They try to send both, and they can't. The packet sending fails for both computers, meaning that both of them have to retry sending their packets (which clogs up the network even more). 

The area where these sort of packet collisions can occur is also called the _collision domain_. With hubs, all of their ports (and connected hubs/devices) are a part of the same collision domain. Here's what the collision domains look like on a network that uses hubs:

![Hub Collision Domains]({{ site.baseurl }}/img/articles/networking-switching/hub-collision-domains.svg "Hub Collision Domains")

This is a big problem, and particularly as the number of computers / traffic grows, packets start colliding at an alarming rate (which slows the whole network down).


### Switches

Switches were created in response to the collision-domain issues present with hubs. On a switch, every single port is a separate collision domain, so if it receives to packets at the same time from different computers, it can handle both.

Let's take another look at the basic layout of a switch:

![Hub / Switch]({{ site.baseurl }}/img/articles/networking-switching/hub-switch.svg "Hub / Switch")

Now each port can be connected to one or more devices (one if a device is connected directly, multiple if a hub/switch is plugged into one of the ports). Packets are addressed to a specific MAC/IP address. When a switch sees a packet come in through a port, the switch stores the MAC address and the port it came in on. Then, it know something like "MAC address XYZ is on port 3".

Whenever a packet comes in, the switch looks at the destination MAC address of that packet. If it knows which port that MAC address is connected to, it only sends the packet out that port.

Here's a diagram showing a switch routing a packet, along with a display of it showing which MAC addresses it knows:

![Switch Packet Forwarding]({{ site.baseurl }}/img/articles/networking-switching/switch-packet.svg "Switch Packet Forwarding")

The switch sees the incoming packet with the destination MAC address `5b:3a`. It knows that this MAC address is on Port 1, so it only sends it out that port. At the same time, it also gets the source MAC address from the packet and records that MAC for port 6.

If the switch doesn't recognise the destination MAC address, it'll just send it out everywhere (similar to a hub) until it learns which port that address is behind.

With hubs, we talked about collision domains. Let's show a quick example of that same network above but with switches, and the resulting collision domains:

![Switch Collision Domains]({{ site.baseurl }}/img/articles/networking-switching/switch-collision-domains.svg "Switch Collision Domains")

In this topology (network layout) there's much less of a chance for packet collisions, they will not nearly affect as many computers, and as a result the network as a whole can be much faster.


## Connecting to the network









