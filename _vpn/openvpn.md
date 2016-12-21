---
layout: page
title: OpenVPN
incomplete: true
order: 6
---


## Architecture

### Transport

UDP is the desired transport for OpenVPN traffic, although it can go over both UDP and TCP. The reason UDP is desired is primarily related to speed – what OpenVPN does is embed TCP/UDP connections inside another connection. If you use TCP for the OpenVPN connection and then try to embed other TCP connections inside it, you get two protocols whose jobs are to ensure data is transmitted correctly. Nesting those produces all sorts of issues and slows down your connection unnecessarily when the OpenVPN protocol itself fixes those sorts of issues.

## Manual Configuration


## Config Overview


## Debugging OpenVPN Log Errors
