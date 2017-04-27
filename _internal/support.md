---
layout: page
title: Support Tool
order: 1
---

The PIA support tool is how we help customers with their accounts, mail servers, and all other sorts of things. The support tool is used a lot in our day-to-day responding to customers, so it's useful to know how it works and what you can do with it.

Let's give a quick overview of how to get into and use it.


## Logging In

When you get to the support tool for the first time, this is what you'll see:

<img src="{{ site.baseurl }}/img/articles/internal-support-tool/login.png" class="fullwidth-bordered" style="width: 499px;"/>

Simply put in the username and password you've been provided with, and you should get to the tool itself.


## Tool Overview

Here's what the tool looks like once you've logged in:

<img src="{{ site.baseurl }}/img/articles/internal-support-tool/overview.png" class="fullwidth-bordered" style="width: 859;"/>

The search bar lets you search for PIA user accounts (and confirm various details such as order IDs), and the buttons at the top let you access additional functionality.

Here's what each button at the top does:

> <i class="fa fa-bug support-icon" aria-hidden="true"></i> Lets you see user-submitted debug logs.
>
> <i class="fa fa-cogs support-icon" aria-hidden="true"></i> Lets you confirm whether a mail server is an open relay.
>
> <i class="fa fa-server support-icon" aria-hidden="true"></i> Lets you add mail servers to our whitelisted servers.
>
> <i class="fa fa-envelope-o support-icon" aria-hidden="true"></i> Lets you whitelist email addresses if they've been blocked.
>
> <i class="fa fa-user-plus support-icon" aria-hidden="true"></i> Lets you create new trial accounts for users.
>
> <i class="fa fa-user-circle-o support-icon" aria-hidden="true"></i> Lets you generate retention (discount) links.
>
> <i class="fa fa-info-circle support-icon" aria-hidden="true"></i> Lets you see when our last payments were to assist when troubleshooting outages.


### Account Lookup

With the support tool, you can lookup accounts in the search bar. This search bar lets you lookup accounts by:

- The name of the account (e.g. `p8458911`).
- The email address associated with the account (e.g. `doaks@londontrustmedia.com`).
- The Paypal/Stripe/etc payment processor transaction ID.
- The last 4 digits of the credit card used to purchase the account.
- The PIA order ID, sent after the account has been purchased.

We allow you to lookup accounts in these ways so that you can confirm provided account details. For instance, if a customer gives you their PIA order ID to confirm they own an account, you can search that ID in the support tool and confirm that their account is shown.

Once you've successfully searched an account, you're able to see the actions that have been taken with that account and do additional things with it. Here's an example of a trial account I've looked up:

<img src="{{ site.baseurl }}/img/articles/internal-support-tool/account-trial.png" class="fullwidth-bordered" style="width: 993px;"/>

At the top you can see _"1 record found, 4 related"_. This indicates that there's four other accounts that use the same email address, and can be useful if users tell you that they've got multiple accounts or are having similar troubles.

Here's the info that's conveyed with each account:

> - Account name.
> - Email address.
> - The type of account it is (trial, monthly renewals, yearly renewals, etc).
> - If generated, the description that was provided when generating the account.
> - Current status of the account, such as "trial active", "account active", "subscription active", etc. Here's a list of statuses and what they mean:
>   - <span class="st-span st-active">trial active</span> means that the account is a trial account, and can currently be used.
>   - <span class="st-span st-inactive">trial inactive</span> means that the account is a trial account, and has expired or been disabled.
>   - <span class="st-span st-active">account active</span> means that the account is a standard account, and can currently be used.
>   - <span class="st-span st-inactive">account inactive</span> means that the account is a standard account, and has expired or been disabled.
>   - <span class="st-span st-active">subscription active</span> means that the account will attempt to automatically renew.
>   - <span class="st-span st-inactive">subscription inactive</span> means that the account will not renew.
> - _Started at_ shows when the account was created.
> - _Ended at_ shows when the account expired, or is due to expire.
> - _Days remaining_ shows how long the customer has left on their current subscription period. When this finishes, it will either expire or renew, depending on whether their subscription is active.

---

Let's take a look at a normal subscription account and the info that's conveyed on it:

<img src="{{ site.baseurl }}/img/articles/internal-support-tool/account-stripe.png" class="fullwidth-bordered" style="width: 1204px;"/>

In addition to the above, there's an extra _"credit card updated at"_ field, and there's also the log table showing the actions that have been taken with this account thus far. This is useful because if you see a large number of previous support actions, a recent instance of the user resetting their password, or something similar, it can help you work out what's going on with an account.

Here's what each column in the log means:

> - **Origin**: If the origin is <span class="st-span st-active"><i class="fa fa-life-ring" aria-hidden="true"></i> support</span> it means the change/action was made by support, and it's <span class="st-span st-good"><i class="fa fa-user" aria-hidden="true"></i> customer</span> if the customer themselves made the change.
> - **Timestamp**: Shows when the action was performed.
> - **Agent/Admin**: Shows which agent made the change (if that information's available).
> - **IP**: Shows the IP address the change was made from. Can be useful if you have a user that's seemingly lost access to their account.
> - **Description**: Description of the change that was made, and any agent/submitted additional info about it.

---

When looking at an account, you have a number of buttons that let you perform different actions on that account. Let's go through what each button means:

> <span class="st-acct-btn">reset pwd / send <strong>activation</strong></span> resets the user's password and sends them the standard activation email containing their username and the new password.
>
> <span class="st-acct-btn">reset <strong>x-login</strong> info</span> resets the x account (e.g. `x8458911`) password.
>
> <span class="st-acct-btn">reset pwd / send <strong>installer links</strong></span> resets the user's password and sends them the new password with app installers.
>
> <span class="st-acct-btn">verify email</span> verifies whether or not the customer's email has been blocked by our systems.
>
> <span class="st-acct-btn">resend invoice</span> sends the customer's last invoice to them via email.
>
> <span class="st-acct-btn">change email</span> changes the email to the one provided in the textbox.
>
> <span class="st-acct-btn">resend <strong>discount</strong> email</span> sends the user a discount renewal email.
>
> <span class="st-acct-btn"><strong>cancel</strong> subscription</span> means the account won't renew at the end of its subscription length.
>
> <span class="st-acct-btn">refund</span> does just that, refunds the customer for their entire latest payment.

If you're looking at a trial account, a number of these buttons will be omitted since you can't, for instance, refund an account that we've generated manually.

### Whitelisting a Mail Server

By default, PIA blocks SMTP traffic to all unknown mail servers (and blocks all traffic using the plaintext SMTP port). To get past this, we can whitelist known-good SMTP servers. After this, clients will be able to contact that server over ports 465/587.

We can only whitelist mail servers by specific IPs, so get the IP address for the mail server. IF you have the hostname, you can run `dig <hostname>` to see the IP addresses associated of the server.

To whitelist a server, first we click the <i style="color:#666" class="fa fa-cogs" aria-hidden="true"></i> icon to confirm whether or not the given server's an open relay. Open relays don't require any authentication and simply forward any mail sent to them, which makes them very uesful to spammers.

Put in the IP address and click the <span class="st-acct-btn">test open relay</span> button. If no open relay's found, then you can continue.

After you've confirmed that the server's fine, click the <i style="color:#666" class="fa fa-server" aria-hidden="true"></i> icon to actually add the mail server to our whitelist.

Enable the _test open relay_ and _add to doc_ checkboxes, insert the IP of the mailserver, add a comment noting the ticket, and then click the <span class="st-acct-btn">add mail server</span> button.

Once this returns, it'll tell you whether it's successfully added the server. If it has, you can let the customer know that we've added it and to wait around 24 hours to try again. As well, you may need to tell them to change the server's hostname to the whitelisted IP address in their email client's configuration (e.g. instead of having `smtp.bigpond.com` they'd use something like `135.23.2.1` which we know has been whitelisted).

### Generating a PIA Account

Sometimes we need to generate PIA accounts. QA uses them to test devices, and PIA employees can use them to test devices. Sometimes we offer extra account time to our customers or creating a new account to recover from certain types of issues, and this is when we also need to generate accounts for them.

To do this, you click the <i style="color:#666" class="fa fa-user-plus" aria-hidden="true"></i> icon to open up the account creation menu. You simply select how long the account should last, put in the email address it'll send account details to, and then put in a reason for creating it. The reason should contain your Slack name, the ticket ID if appropriate, and a quick explanation as to why it's been created.
