---
layout: page
title: MTR Tests
order: 10
---
An MTR test is a quick, simple way to test a variety of network issues and discover related faults. What an MTR test does is give you a good insight into the connection between two endpoints, and the routers inbetween.

To start off, let's go over two related tools, **ping** and **traceroute**.


## Ping

Ping is one of the basic network tools out there. What it does is send a single packet to the destination, and the destination sends a single-packet reply to confirm it got the message. Most tools do this multiple times, recording how many replies they received vs how many they sent (and as a result, how many packets were dropped along the path).

Essentially, what a ping measures is:

* **Reachability**: Can the two endpoints successfully reach each other?
* **Packet Loss**: How many packets arrive successfully, and how many do not?
* **Delay (Latency)**: By looking at how long it is between sending a query and getting a response, we can measure how slow the connection is.

Let's look at the output of an example ping command:

    $ ping example.com
    PING example.com (93.184.216.34): 56 data bytes
    64 bytes from 93.184.216.34: icmp_seq=0 ttl=52 time=184.027 ms
    64 bytes from 93.184.216.34: icmp_seq=1 ttl=52 time=294.038 ms
    64 bytes from 93.184.216.34: icmp_seq=2 ttl=52 time=397.321 ms
    64 bytes from 93.184.216.34: icmp_seq=3 ttl=52 time=356.257 ms

    --- example.com ping statistics ---
    4 packets transmitted, 4 packets received, 0.0% packet loss
    round-trip min/avg/max/stddev = 184.027/307.911/397.321/80.423 ms

In this example, we can see that the IP address found for `example.com` is `93.184.216.34`. Our machine sends ping packets that contain 56 bytes of data.

Each time we receive a reply packet, the time it's taken to get there and come back, and the TTL that we see on the reply packet. Here, we can see that the TTL is 52. Given that the default TTL in use is 64, `example.com` is likely around 12 hops away. As well, the time on each packet varies wildly but it averages around 300 milliseconds of delay.

After the tests are completed it shows how many packets were transmitted, received, and the percentage of packet loss as a result. It also shows some statistics about the time it took for packets to get back.

With this information, we can work out how lossy and slow the connection is, and whether we can reach the endpoint at all.


## Traceroute

Traceroute is another of the basic networking tools out there, and helps work out further issues along the path.

The main thing to understand is that if a TTL runs down to zero, a reply is sent back to the source essentially saying "This packet has been dropped by <IP>". Now, what some enterprising Internet designers worked out was that if you sent a series of packets, with the MTU starting at "1" and incrementing it for each packet, you could use the replies to map out exactly which routers a packet was going through to get to the destination.

Essentially, the first packet has a TTL of 1, so you send it, your router receives it, decrements the TTL, and then sends that error message back to you. Now you have the IP of your router, know how far away it is, and know the speed of the connection between you and that destination. Set the TTL to 2, send it off, and you'll get the same info about your ISP's router.

Let's take a look at an example traceroute command:

    $ traceroute example.com
    traceroute to example.com (93.184.216.34), 64 hops max, 52 byte packets
    1  172.20.10.1 (172.20.10.1)  4.711 ms  4.100 ms  3.518 ms
    2  * * *
    3  * * *
    4  bundle-ether12.woo-edge901.brisbane.telstra.net (165.228.103.61)  29.434 ms  70.417 ms  19.633 ms
    5  bundle-ether5.woo-core1.brisbane.telstra.net (203.50.11.136)  31.131 ms  83.011 ms  27.554 ms
    6  bundle-ether11.chw-core10.sydney.telstra.net (203.50.11.70)  40.650 ms  56.075 ms  43.905 ms
    7  bundle-ether1.oxf-gw11.sydney.telstra.net (203.50.6.93)  55.539 ms  31.179 ms  41.073 ms
    8  bundle-ether1.sydo-core03.sydney.reach.com (203.50.13.98)  39.494 ms  84.740 ms  38.228 ms
    9  i-0-1-0-17.sydo-core04.bi.telstraglobal.net (202.84.222.62)  40.255 ms
        i-0-1-0-15.sydo-core04.bi.telstraglobal.net (202.84.222.54)  54.194 ms
        i-0-1-0-18.sydo-core04.bi.telstraglobal.net (202.84.222.66)  46.589 ms
    10  i-0-7-0-4.1wlt-core01.bx.telstraglobal.net (202.84.144.82)  210.560 ms  185.360 ms  448.043 ms
    11  i-0-0-0-2.tlot02.bi.telstraglobal.net (202.84.251.185)  237.990 ms
        i-0-0-0-3.tlot02.bi.telstraglobal.net (202.84.251.189)  189.789 ms
        i-0-5-0-1.tlot02.bi.telstraglobal.net (202.84.253.38)  215.167 ms
    12  * * *
    13  core1.cpm.edgecastcdn.net (108.161.249.17)  397.573 ms  238.043 ms  184.599 ms
    14  93.184.216.34 (93.184.216.34)  180.101 ms  379.858 ms  183.410 ms

As we can see here, the first hop -- or the closest router to us, is `172.20.10.1`. This is our ISP's local router, the one that talks directly to us.

On hops two and three, we see what's commonly referred to as "stars". Essentially, rather than returning the error reply noted above, these two routers instead silently drop the packets. Because of this, we know that these routers exist, but can't obtain any further information about them.

Going further, we can see the packet transit through:

1. Telstra's Brisbane routers.
2. Telstra's Sydney routers.
3. Onto Telstra's core global backbone.
4. Through some hidden transit router.
5. Onto Edgecast CDN's network.
6. Finally, to the end machine that handles example.com.

For hops 9 and 11, we can also see multiple hostnames pop up. This means that our packets ended up on different routers for those hops. What's likely going on here is that Telstra's global backbone has multiple redundant paths, and the packet ends up going through a random core link/router at these hops.

This gives us a whole lot of information. We can see exactly where the packet's going, and on average how slow each connection is. However, we can't see information such as packet loss for each of these hops, and that means we're missing a vital piece of information that can indicate issues.

That is where MTR comes in.


## MTR

MTR stands for "My Traceroute". Where ping and traceroute have been tools almost as long as the internet itself has existed, MTR is a fairly recent creation.

Essentially, MTR is a traceroute that also shows the packet loss for each hop (along with other useful information).

Let's take a look at an example MTR command:

                                        My traceroute  [v0.87]
    MacBook-Pro.local (0.0.0.0)                                                 Sat Nov 26 07:39:26 2016

                                                                Packets               Pings
    Host                                                      Loss%   Snt   Last   Avg  Best  Wrst StDev
    1. 172.20.10.1                                             0.0%   131    4.1   4.0   2.0  26.2   2.3
    2. ???
    3. ???
    4. Bundle-Ether12.woo-edge901.brisbane.telstra.net         0.8%   130   31.7  30.0  18.5 107.9   9.0
    5. bundle-ether5.woo-core1.brisbane.telstra.net            0.8%   130   32.8  30.1  19.6  48.6   5.0
    6. bundle-ether11.chw-core10.sydney.telstra.net            0.0%   130   46.5  41.8  32.4  76.0   5.4
    7. bundle-ether1.oxf-gw11.sydney.telstra.net               0.8%   130   38.7  42.8  32.6  92.8   6.1
    8. bundle-ether1.sydo-core03.sydney.reach.com              0.0%   130   44.4  44.1  30.4 191.3  14.1
    9. i-0-1-0-18.sydo-core04.bi.telstraglobal.net             0.0%   130   42.2  43.7  35.9 118.9   7.7
    10. i-0-7-0-4.1wlt-core01.bx.telstraglobal.net             0.0%   130  180.2 180.2 169.1 262.6   8.2
    11. i-0-0-0-3.tlot02.bi.telstraglobal.net                  0.0%   130  178.8 184.6 174.2 214.9   4.7
    12. ???
    13. core1.cpm.edgecastcdn.net                              0.0%   130  188.3 188.5 173.9 252.9  12.1
    14. 93.184.216.34                                          0.8%   130  184.9 184.9 175.6 211.8   4.9

Here, we ssee the same information that we found in the traceroute above. However, we can also see:

* How many packets were sent (in the **Snt** column).
* How many packets failed to return as a percentage (in the **Loss%** column).
* Details about the delay packets experience getting to the hop and back (under the **Pings** header).

From the MTR test above, we can see that the link from hop 9 to hop 10 is a very slow link -- it adds around 140 milliseconds of delay to the connection! The most reasonable explanation is that this link goes through an undersea cable, resulting in what looks like a slow link.

With this information, it's easy to see where exactly in a path between two machines that an error occurs. That includes whether it's closer to your side, to the destination's side, or here where it's in the middle.

<div class="advanced">
	<p><strong>Tier 1 Providers</strong></p>
    <p>As you look at more MTR tests, you'll start to see names like Level3, Cogent, Verizon, Sprint, and other providers. These are what we call "Tier 1 Providers", or the providers that run parts of the core of the internet.</p>
    <p>Regular providers either pay or charge for traffic going over their links — say your ISP charging you for the data that you send over their network, or if you host a webserver you may need to pay X for 100GB of data transfer, Y for 500GB of data transfer, etc. Tier 1 networks don't charge for traffic, simply because it's within their best interest to freely establish links with both all the other Tier 1 providers and with large web services such as Google and Amazon.</p>
</div>

Because MTR deals with percentages of packet loss, it's best to wait for around 100 packets to be transmitted before putting trust in the packet loss result. Because one packet that's lost due to a momentary glitch can look like a very concerning level of error until you work out what's going on.

What we can see in the MTR test above is that the packet loss is `0.8%` for a number of hops, but between all of them the packet loss goes back to `0%`. This simply means that particular router had an issue receiving the packet, but the rest of the path doesn't have that issue. When there's packet loss to worry about, generally you will see packet loss start at one hop and similar levels of loss continue for the rest of the links, such as with this example test:

                                        My traceroute  [v0.87]
    MacBook-Pro.local (0.0.0.0)                                                 Sat Nov 26 07:39:26 2016

                                                                Packets               Pings
    Host                                                      Loss%   Snt   Last   Avg  Best  Wrst StDev
    1. 172.20.10.1                                             0.0%   131    4.1   4.0   2.0  26.2   2.3
    2. ???
    3. ???
    4. Bundle-Ether12.woo-edge901.brisbane.telstra.net         0.8%   130   31.7  30.0  18.5 107.9   9.0
    5. bundle-ether5.woo-core1.brisbane.telstra.net            0.8%   130   32.8  30.1  19.6  48.6   5.0
    6. bundle-ether11.chw-core10.sydney.telstra.net            0.0%   130   46.5  41.8  32.4  76.0   5.4
    7. bundle-ether1.oxf-gw11.sydney.telstra.net               0.8%   130   38.7  42.8  32.6  92.8   6.1
    8. bundle-ether1.sydo-core03.sydney.reach.com              0.0%   130   44.4  44.1  30.4 191.3  14.1
    9. i-0-1-0-18.sydo-core04.bi.telstraglobal.net             0.0%   130   42.2  43.7  35.9 118.9   7.7
    10. i-0-7-0-4.1wlt-core01.bx.telstraglobal.net             31.2%  130  180.2 180.2 169.1 262.6   8.2
    11. i-0-0-0-3.tlot02.bi.telstraglobal.net                  34.8%  130  178.8 184.6 174.2 214.9   4.7
    12. ???
    13. core1.cpm.edgecastcdn.net                              33.3%  130  188.3 188.5 173.9 252.9  12.1
    14. 93.184.216.34                                          35.9%  130  184.9 184.9 175.6 211.8   4.9

In this example, we can see that the packet loss starts on hop 10, and continues all the way to the end. This likely means that there's an issue with the undersea cable linking routers 9 and 10 together, and that's causing packet loss across the connection. As well, congestion and DDoS attacks can also commonly cause similar issues -- since there's such a large number of packets trying to get through, routers just start dropping them at some point.


### MTR on the VPN vs not on the VPN.

Let's talk specifically about VPN connections. Particularly, when doing an MTR test both while not using the VPN, and another test while on the VPN.

When you're not using the VPN and doing a test to our servers, you're checking for issues between your computer and our VPN server.

However, when you're on the VPN and testing to a destination, you're testing for issues between the VPN gateway and that destination site.

Both of these can be very useful in working out issues. If there's an issue between your computer and the VPN server itself, that can degrade the VPN connection and cause problems. If, on the other hand, there are troubles from the VPN server to the destination, there's generally not much for us to do besides try to talk to that destination site.

One thing to keep in mind is that when you're connected to the VPN, the VPN presents itself as the first hop in your connection to any host. As an example:

                                        My traceroute  [v0.87]
    MacBook-Pro.local (0.0.0.0)                                                 Sat Nov 26 08:05:48 2016

                                                                Packets               Pings
    Host                                                     Loss%   Snt   Last   Avg  Best  Wrst StDev
    1. 10.87.10.1                                             0.0%   109  221.5 220.3 200.2 258.4  22.7
    2. host.my-tss.com                                        0.0%   109  237.1 217.1 198.7 246.4  18.7
    3. 104.200.152.56                                         0.0%   109  204.8 228.4 195.8 297.2  36.1
    4. 78.152.32.112                                          0.0%   108  206.1 208.6 194.2 244.5  15.4
    5. edgecast-networks.as15133.any2ix.coresite.com          0.0%   108  206.4 213.6 200.4 255.2  18.4
    6. 93.184.216.34                                          0.0%   108  216.2 212.7 194.1 242.3  17.4

As we can see here, that first hop (`10.87.10.1`) is the VPN server itself. If we see packet loss on this first hop, it can indicate errors in the VPN configuration itself.

This test also shows the differences in routing when using a VPN vs when not using a VPN. The original test above transited Telstra's local network, Telstra Global, and finally to Edgecast. Here, however, it transits through the VPN server, My-TSS, some transit routers, and finally to Edgecast.

<div class="advanced">
	<p><strong>Falsified Domain Names</strong></p>
    <p>As a note, that second hop (<tt>host.my-tss.com</tt>) is likely falsifying its IP address / hostname, in an attempt to prevent people from finding out the IP address of that router and prevent DDoSes to it.</p>
    <p>We can see this because <tt>host.my-tss.com</tt> doesn't have anything in the way of in-depth router identification information as most other hostnames do. This is relatively common in various places around the internet, and is perfectly normal.</p>
</div>


## Overall

Ping tests:

* Reachability.
* Packet loss.
* Latency.

Traceroute tests:

* The route between two endpoints.
* Latency.

MTR tests:

* Reachability.
* Packet loss.
* Latency.

And it tests all three of these things for every single hop in the path.

MTR tests while not on the VPN test the connection between the endpoint and the VPN gateway.

MTR tests while connected to the VPN test the connection between the VPN server and the destination.
