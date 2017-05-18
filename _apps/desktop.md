---
layout: page
title: Desktop
order: 1
---
Our desktop app is used on Windows, Mac and Linux. This page was last updated for v70 of our desktop app.

<div class="video-notice">

There's also a video version of this article here:
<video controls>
    <source src="{{ site.baseurl }}/videos/apps/desktop-app-overview.mp4" type="video/mp4">
    <source src="{{ site.baseurl }}/videos/apps/desktop-app-overview.mkv">
</video>
</div>


## Installing

So this is what the PIA installer file looks like on Mac machines after it's downloaded:

<img src="{{ site.baseurl }}/img/articles/apps-desktop/install-mac.png" class="fullwidth" style="width: 731px;"/>

Once you double-click the installer, it opens up to this page which lets you actually install the app:

<img src="{{ site.baseurl }}/img/articles/apps-desktop/install-splash-mac.png" class="fullwidth" style="width: 912px;"/>


## Tray Icon

When you right-click the tray icon, a list of servers and options pops up. This is what shows when you click it on Mac:

<img src="{{ site.baseurl }}/img/articles/apps-desktop/dropdown-menu-mac.png" class="fullwidth-bordered" style="width: 267px;"/>

Let's go through what each of these buttons does.

### Connect & Disconnect

This just has the connect and disconnect buttons, which are used to control whether the VPN connection is active or not.

### Server List

This section lists all the servers that we have available, making it easy for our users to look down the list and connect to a specific server.

### Settings

This button opens up the main PIA settings menu.

### Send Slow Speed Complaint

This button sends a complaint to our networking team that current server the app is using is slow.

### Help

This button sends the user to our support site where they can get further assistance.

### Exit

This button (hopefully) closes the PIA app and disconnects from any connected servers.


## Settings Menu

When you open up the settings of the PIA app, this is what users first see:

<img src="{{ site.baseurl }}/img/articles/apps-desktop/app-main-mac.png" class="fullwidth" style="width: 417px;"/>

Here's what each textbox and checkbox on the menu means:

- **Username** is the PIA username (e.g. `p1234567`).
- **Password** is the password for their account.
- **Forgot Password** sends the user a link to reset their password.
- **Start application at login**: When this is enabled, the PIA app will startup when the computer starts.
- **Auto-connect on launch**: When this is enabled, the app will automatically connect to the VPN when it's started.
- **Show desktop notifications**: When this is enabled, the app will display notification boxes when the VPN is connected or disconnected.
- **Region**: This dropdown selects the region which is connected to (e.g. Australia, Japan, California).
- **Language**: This dropdown changes what language the PIA app is displayed in.
- **Advanced**: When this is pressed, the app opens up to show advanced settings.
- **Save**: When this is pressed, the updated settings (including username, password, checkboxes and dropdowns) are saved.

### Advanced Settings

When the **Advanced** button is selected, the full settings menu opens up to display this:

<img src="{{ site.baseurl }}/img/articles/apps-desktop/app-settings-mac.png" class="fullwidth" style="width: 762px;"/>

Here's what each of the advanced settings means:

- **Connection Type**: This selects what type of connection is used for the VPN. `udp` is the default and fastest, `tcp` is a bit slower but can work in cases where `udp` fails.
- **Remote Port**: This selects the 'VPN port' used for connections. If `auto` does not work (or does not work well), you can switch through each port in turn to see which works best for you.
- **Local Port**: This is a fairly complex option used to set the 'local port' that the VPN connects with. You won't need to worry about this unless you're doing something extremely in-depth and unique.
- **Request Port Forwarding**: When this is enabled, the PIA app requests a port. This is primarily useful for torrent clients, but can also be necessary for other types of apps.
- **PIA MACE**: When this is enabled, ads and malware (viruses) are blocked when the VPN is enabled. Note that this isn't a complete block, but should prevent most ads and bad websites from loading while the user's connected to PIA.
- **VPN Kill Switch**: When this is enabled, the computer can only access the internet when the VPN is connected. If the VPN connection drops, the user won't be able to access the internet. This is useful while running overnight, when you don't want a momentary connection failure to result in your IP being exposed.
- **IPv6 Leak Protection**: This should be enabled and stay enabled. This prevents a way that users' real IP addresses can leak out, even while connected to the VPN.
- **Use Small Packets**: If a user is having trouble using the VPN, they can enable this setting. It uses a different form of connecting that works better through some devices.
- **Debug Mode**: If this is enabled, the PIA app will save debugging information. This information is useful for us (and very technical users) to resolve certain in-depth issues.

### Encryption Settings

After enabling **Advanced Settings**, you'll see two buttons appear on the left – "Simple" and "Encryption". Clicking on **Encryption** enables the encryption settings, which lets you change how secure your VPN connection is.

Here's what the encryption settings look like:

<img src="{{ site.baseurl }}/img/articles/apps-desktop/app-encryption-mac.png" class="fullwidth" style="width: 762px;"/>


We have some in-depth information on the encryption options our app provides on our website [here](https://www.privateinternetaccess.com/pages/vpn-encryption).


## Overview

After installing our application, the settings menu pops up which lets you input your username and password. Your details and changes are only saved if you specifically click the Save button.
