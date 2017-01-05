---
layout: page
title: TLS / SSL
incomplete: true
order: 5
---
Transport Layer Security, or TLS, is essentially one of the main ways to create secure connections between machines today.

SSL (or Secure Sockets Layer) was what existed before TLS. The difference is that SSL has been broken for a few years now, where the recommended versions of TLS are fine.

From the TLS documentation itself, the goal of TLS is to provide connections that have:

- **Authentication**: The server's identity should _always_ be assured.
- **Confidentiality**: Only the machines at either end can see the raw data being sent over the TLS connection.
- **Integrity**: Data sent over the TLS connection can't be modified by anyone in the middle.

As well, TLS is specifically designed to have these even if someone is between the two machines (such as your network admin or your ISP).
