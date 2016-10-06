---
layout: page
title: Linux Core Concepts
order: 3
---
This article goes over core concepts that should help you better understand how Linux works underneath the hood.

<div class="video-notice">

There's also a video version of this article here:
<video controls>
    <source src="/videos/computers/linux-core-concepts.mkv">
</video>
</div>

---


### OS Fundamentals

At a very high level, Windows, Mac, and Linux-based operating systems are all split up in this sort of way:

* **Kernel**: Interfaces with the hardware and provides a nicer interface for the rest of the system to talk to.
* **System Software**: Works closely with the kernel and provides much of the system internals required for user apps to work. This includes things like the program that displays the desktop itself.
* **User-level Apps**: This includes both apps bundled with the operating system (such as Safari on OSX or Notepad on Windows), and apps installed by the user themselves.

For a more visual explanation, here's what this sort of typical OS layout looks like:

![OS Layout](/img/articles/computers-linux/os-layout.svg "OS Layout")

In a way, the kernel _abstracts_ the hardware, the system software _abstracts_ the kernel, and the user-level apps are what people actually use to get work done (user apps communicate with both the system software and occasionally the kernel to accomplish their tasks). The operating system bundles some user apps with it (such as Notepad on Windows or Safari on OSX), and the other user apps are installed afterwards (such as Firefox, Google Chrome, or Adobe Illustrator).

The typical set of software for a full operating system includes the kernel, system software, and a few user-level apps. Without this full set of software, users can't get work done with a computer.

Both Windows and Mac come with this full set of software. If you take a Windows disk and install it to a computer, that's exactly what you'll get. However, Linux itself is just the kernel. "Linux" is not a full operating system, just a free kernel for the rest of the system to build on top of.

Here's a picture showing the differences between Windows/Mac and Linux, and how Linux itself is not an operating system.

![OS Suite](/img/articles/computers-linux/os-suite.svg "OS Suite")


### Distributions

As described above, Linux itself is not an OS. It doesn't contain the system software or user apps that let regular people use it.

Distributions are collections of the kernel, as well as a set of system software and user apps that work well together. A distribution is a full operating system, and contains all the parts that people need in order to use Linux on their computer.

A Linux distribution is roughly equivalent to Windows or OSX. You can burn a release of a distribution to a DVD, then put it in your computer and install it just as you can put a Windows DVD into your computer and do the same.

![Distro Suite](/img/articles/computers-linux/distro-suite.svg "Distros")

There are many different Linux distributions – each with their own desktop, system software, quirks and methods of operation. Because of this, it's very difficult to write a set of instructions that works with a majority of Linux installs out there.

The main Linux distributions that people use today are Ubuntu and Fedora, but there are a large number of alternatives that people install and use every day.

![Distributions](/img/articles/computers-linux/distributions.svg "Distributions")

Linux distributions can also be based on (or 'source' from) another distribution. For instance, Linux Mint is based on Ubuntu. Because of this, a great deal of the Ubuntu commands work with Mint, and Mint can install the same software that Ubuntu can. Ubuntu could be referred to as "Linux Mint's upstream distribution".

<div class="advanced">
	<p><strong>Upstreams and Bugs</strong></p>
	<p>If a bug is found in Linux Mint, and the cause of the bug is found to be a fault with Ubuntu, who should fix the bug?</p>
	<p>Typically, fixes should get applied as far 'upstream' (towards the initial source) as possible, as those fixes will then be picked up by the other distributions that use the software.</p>
	<p>Similar reasoning is used for bugs found in user apps and reported to distributions. If a bug is reported with Linux Mint and the bug is with a user app, typically the distro developers will ask the user to report the bug to the app development team directly (sending the bug upstream).</p>
</div>


### Packaging

With Windows and Mac, you can't change the system software and packaged user apps. On the other hand, Linux is designed to let you do so. Similar to user apps, in Linux the system software is just made up of a collection of separate programs (any of which you can remove or replace with an alternative).

In Linux, a package is just a collected bundle of software, configuration files and documentation. Linux simplifies the management of which software is installed (that is, which packages are installed) through package management.

![Anatomy of a Package](/img/articles/computers-linux/package.svg "Anatomy of a package")

Many different people have proposed ways to store packages. However, there are two primary ones in use today:

* **deb**: The 'Debian' packaging format. deb packages are managed with `apt-get` and `aptitude`.
* **rpm**: The 'RedHat Package Manager' packaging format. rpm packages are managed with `yum` and `dnf`.

The package management system is an integral part of a Linux distribution, and the package manager in use strongly defines how users interact with the system.

<div class="advanced">
	<p><strong>What is a Rolling Release?</strong></p>
	<p>Most distros make a release every few months, or a few times a year. For each release of their distro, they manage a separate set of packages. This is typically done to help increase stability and reduce the likelihood of things breaking while updating software.</p>
	<p>'Rolling Release' refers to a package management system where instead, only one set of packages is kept &ndash; the latest. Whenever you update, you get the entire set of new software (which means that the core software that runs your OS is contantly being updated).</p>
	<p>The main upside of rolling release distros is that they are typically much more up-to-date than regular distros.</p>
	<p>The main downside of rolling release distros is that there is a higher chance of them breaking while updating, since they update the core software used in your OS much more often than regular distros would.</p>
	<p>There are upsides and downsides to either approach, but at this point rolling release distros are not as commonly-used as regular ones.</p>
</div>


### Overview

* Operating systems are made up of the kernel, system software, and bundled user apps.
* Linux is just the kernel, whereas a distribution contains the kernel, system software and bundled user apps.
* Distributions differ in many different ways, from their desktops to their packaging systems.
* A package is a bundle of software that can be installed, removed, or replaced with another package.
* Debian-based distros use `apt-get`, Fedora-based distros use `yum` and `dnf`.
