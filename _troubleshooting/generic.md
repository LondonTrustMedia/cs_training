---
layout: page
title: Generic TS
display: Generic Troubleshooting
order: 1
---
With computers, we use the word 'system' a fair bit: your phone runs an operating system; your whole computer itself, from Windows to the motherboard, is one big system; and the process of running a program and getting some output can also be thought of as a system.

In technical support, our main job is to help people fix systems. Knowing exactly how to approach an issue, where to look for the root cause, and figuring out how to solve it, are all very useful.

This section goes through how to solve issues with systems in general. Whether the system is a VPN connection, a computer, or even a  water leak, these steps should help you approach issues in a useful way, and learn how to resolve them.


### Terms

These are just a few terms that are well-used in troubleshooting.

- **System**: The machine, software, or process that we're trying to fix.
- **Issue**: A problem that's stopping the system from working correctly.
- **Root Cause(s)**: The primary cause of an issue.
- **Resolve**: Fix.

We'll be using these terms here a fair bit.


---


## How to Troubleshoot

When we see an issue with a system, our job is to resolve it and get the system working successfully. To do so, you need to discover the root cause of the issue. Once we know what the root cause is, we're able to find the next steps towards resolving it.

Here's a general process to troubleshooting issues:

1. Issue is happening.
2. Gather and read through information about issue.
3. Find possible root cause.
4. Solve the root cause.
5. Check whether issue is resolved.
    1. If it isn't resolved, go back to step 2.
6. Issue resolved!

There are a few steps here which are simplified and questions which need answering, so let's go through those now.


### Getting information about an issue

When dealing with customer requests, there are a few ways to do this.

The primary way is to look at everything the customer's sent to you so far. If there's a ticket, read every response to get relevant information. If it's a social media inquiry, see whether they've made any other posts or topics discussing the issue in more detail, and simply dig into what they've sent to us to get all the info you can about it.

The next step, if you do need more information, is to simply **ask the customer**. This is a very useful tool in getting information about a problem, and so long as you're not asking unnecessary information, or requesting information that's already been asked, they should be happy to help you out.


### Finding possible root causes

This is where knowing how the system works can really help you out. Knowing how the network, the application, and the device itself works gives you good starting points to start investigating.

Finding causes involves reading information about the issue, and finding where in the system the issue's (likely) happening. From there, you can find why it's happening – a cause that explains the issue or some part of it, and see what's the most likely cause.

Good things to look at here are:

- Software logs: Typically contain information about how the software acts just before and after the failure.
- Screenshots: Seeing exactly what the customer does before/after the failure can in some cases help explain what's going on.
- Exact error messages: Having exact error messages to refer back to can help you better discover what's going on and which part of the system's failing.
- Reproduction: You won't be able to do this a lot of the time, but getting onto a computer/prone/router and running into the issue yourself can help you test possible causes.

Once you've found what you think is the most likely cause, you can present the user with a way to solve it.


### Solving the root cause

Each solution will be different, and in many cases the solution will boil down to some combination of:

- Restart your machine.
- Reinstall the application.
- Try using an alternate piece of software (i.e. stock OpenVPN rather than our app).

When presenting solutions to a user, we should aim to give them clear steps they can go through and refer back to if need be. A large part of our job is also knowing how technical the customer we're talking to is. If the user's more technical, they can generally handle more complex instructions. If they're less technical, we should aim to given them more precise, simple instructions.

Tailoring the given steps can help the customer better understand what we'd like them to do, and from there help them more quickly resolve their issue.


### Seeing whether the issue was resolved

Once we go through a solution, the next step is to see whether the solution actually solved the issue.

If the solution **did** solve the issue, then our possible root cause was correct!

If the solution **did not** solve the issue, then we need to look over our information again, collect more information if necessary, and find the next most-likely root cause.

For some issues, it's perfectly expected that you might go through a couple possible causes before finding the right one. Over time, and as you learn more, you should be able to better know which causes are more and less likely.


### Issue Resolved

Once we've resolved an issue, we're done! We can simply say that we're glad it's working, ask the user if there's anything else we can help them with, and finish off the conversation.
