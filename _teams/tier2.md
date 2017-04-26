---
layout: page
title: Tier 2
display: Tier 2 Teams
order: 2
---
Tier 2 is where tickets go when they can't be handled by the Tier 1 team for whatever reason, or where a ticker requires more careful handling. Our job in Tier 2 is to make sure that we solve the tickets that get assigned to our team, and to assist Tier 1 when possible.


## Our Role

Our job is to be the second line of PIA support, the people that our customers see when their query is either advanced or hasn't been handled appropriately. There's a few reasons why a ticket might be directed towards us:

- It hasn't been correctly handled by the tier 1 team and requires more careful, in-depth, knowledgable responses.
- It requires more in-depth technical, account or payment knowledge than tier 1 can provide.
- We just want to ensure that this customer is handled with more care than has been provided.

We should be equipped with the skills and knowledge to better respond to tickets, and make sure that we can approach and handle whatever queries that come our way.


## Our Responsibilities

There are a few different T2 teams, including the general T2 CS team and T2 Tech. The T2 CS team handles escalated billing/payment queries, and the T2 Tech team handles escalated technical queries.

Each team has different tasks, but the general roles that we handle are investigating and escalating trends / issues, and solving tickets. Here, we give a bit of an overview of the responsibilities we have.


### Solving Tickets

We should be able to solve most all of the queries that come our way. The issues we get pulled into range from strange in-depth technical trouble to simple install/payment issues that haven't been handled correctly.

Being able to take a concerned or irritated customer and provide them with a response that makes them want to give us another chance is vital. In the CS training on the left we go through these sort of situations. As well, just generally how to construct a good response is useful, particularly as we handle public responses more than the other agents.


### Investigating Escalated Trends and Issues

Trends and issues are essentially things that seem odd or wrong. Things such as _"There are a lot of people having issues connecting to U.S. East today"_ or _"The PIA website is down"_. As T2, these trends and issues may be brought to you to make sure they're issues before we escalate them further to management.

Here, we go through how to generally see an issue, test it, and then escalate it appropriately if it's something management should be aware of.

These sorts of issues are generally brought to us by T1 or the T1 supervisor on shift, by a ping in one of the channels or just by someone wandering over and asking you to check it out. However, if you do notice something like this yourself feel free to go through the same process.

When you encounter something you need to investigate, post in your main T2 channel that you're looking into the trend or investigating the issue. A note like this could work well:

> Hmm, it looks like there's a lot of people having issues with U.S. East today. I'm going to investigate and see what I can find.

How you investigate each issue will differ, but generally involves collecting a list of tickets that have the issue. When or while you're getting that list together, here are some examples of specific testing you can perform:

- For one of our gateways having problems, you should find a specific IP that's encountering trouble and perform an MTR on it to check for packet loss and similar
- For payments failing, you could try putting through a test payment with a new card and email address, to see if that completes successfully.
- For something like an OS update affecting the app, you should try updating the test device to see if you can replicate the problem once that's on the new version.
- For the website being down, you should just open up a browser and see whether you can load the website or not. Seeing exactly how the site fails (whether it times out, gives you a 503 / 404 error, etc) can also help the web team figure out the specific trouble with it.


### Escalating Trends and Issues

If you find that something is legitimately a problem and you have details to back it up, you can escalate it to management.

To do so, in the relevant Tier 2 channel, post a message including the handle `@ltm` that details the problem and what's going on. At the same time, take a look at our [escalation document](https://example.com) so you can see how to best reach management if that does not work.

As an example, a message like this quickly and consisely shows what's going on:

---

> **@ltm** It looks like our U.S. East gateway has packet loss of around 50%. We've seen the issue in these tickets:
>
> [https://londontrustmedia.zendesk.com/agent/tickets/1234](#escalating-trends-and-issues)
> [https://londontrustmedia.zendesk.com/agent/tickets/2345](#escalating-trends-and-issues)
> [https://londontrustmedia.zendesk.com/agent/tickets/3456](#escalating-trends-and-issues)
>
> And the attached MTR shows the same.

With this text attached:

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
    14. 203.0.113.231                                          53.2%  130  184.9 184.9 175.6 211.8   4.9

---

With this sort of message, management can see the issue and start taking a closer look at exactly what's going on with that server.





