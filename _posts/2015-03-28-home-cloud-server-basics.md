---
layout: post
title: "Some basics of running your own (cloud) servers"
date: 2015-03-28 +1000
comments: true
---

# 1. It's not hard

Just what the title says - it's really not hard :-)  

The software available to run your servers with (both OS and application) have matured massively over the last decade, and there are hundreds if not thousands of people on the interwebs willing to offer support in some form or another.  For that matter, it's extremely unlikely that you will run into issues that have not been addressed by others, and answers are usually a well-worded google away.

Online resources abound in the form of forums, knowledgebases, FAQs, e-books (free and paid), chat rooms, etc.  They also tend to cater for people of various levels of experience.  One of my favourite sayings applies here - **the only stupid question, is the one you didn't ask**.  Even if the answers aren't always worded nicely, you will learn from it.

---

# 2. Benefits

Apart from learning new things, there are a number of benefits to running your own servers:

_Your data is your own_

By storing your data on a server that you control, there are no risks of running foul of international data search-and-seizure laws.  Your data will also not be collateral damage in the case of massive security breaches, password leaks, lax security measures, or targeted hacking attempts (unless you're the one being hacked, of course).  Though this security-through-obscurity approach is often frowned upon, you generally won't be targeted if nobody knows that your server exists.

_You have control over who has access_

Whether it is work documents or photos of your cat, you can control who sees them and who can modify them.  There are also no issues with changing privacy statements allowing people access, with no prior warning.  You can give and revoke access easily and quickly, to anyone.

_Managing your data life cycle becomes easier_

By having all your data in one location, hosted with open source software, it becomes easier to backup, easier to synchronise across multiple devices, easier to migrate, should you choose to do so, and will not be subject to public cloud services shutting down.

_It can actually save you money_

Depending on the level of service you use from public cloud providers (free vs premium), running open source software on your own power efficient hardware could cost you less per year than paying for numerous services.

**Of course, these benefits can be negated in an instant if you don't take heed of some of the other basics here (#3 and #4 specifically).**

---

# 3. Security

A responsibility that will now fall on your shoulders, is security of your infrastructure and data.  If done properly, it's not all that hard though.  Generally, by using well-maintained open source software, security vulnerabilities will be patched if you keep the software up to date.  Other things, like setting up users and network access, need only be done once if done properly.

_Network access_

This includes items like setting up firewalls, closing ports, forwarding ports, etc.  The approach in this series of articles follows one of minimal external access via VPN and SSH to reduce the possible area of attack.

_Authentication_

User and computer authentication can be as easy or as hard as you decide to make it.  This will generally be a function of how important or sensitive your data is, and how many people will have access to your server.  Options include:

* Username and password
* Username and private keys
* Two factor authentication
* HTTPS with client side authentication

_Physical access_

A common maxim is that all bets are off if an attacker gains physical access to a computer.  

This is no less true when running your own servers.  Security measures taken will likely reflect the importance of your data and the likelihood that someone will want access to it.  For most people though, the biggest concern will be hardware stolen during normal burglaries.  In this case, it's unlikely that they will be after your data, and you can restore from the backups you've made.

---

# 4. Backup, Backup, Backup!

The importance of backups can not be overstated here.

In a sense, by not using public cloud servers, you are now putting all your eggs in one basket.  This is not a bad thing, as long as you are prepared.  Regular incremental and/or full backups (stored locally, but preferably off-site) are not hard to do, but absolutely essential when you are actively storing all your information in one location.

A useful side-benefit is acquiring an awareness of how fickle storage systems can be, and becoming more proactive about backing up ALL your data in other locations.

It should also be pointed out that this process is remarkably easy to automate.

Don't be one of the people who start worrying about backups 10 seconds after you realise your drive failed (data recovery is **VERY** expensive, and not fool-proof).

**_Backup vs Redundancy_**

It is important to note that backup and redundancy **are not the same things**.  While prudent, storing your data on a redundant drive setup (local RAID, NAS, etc), will only protect against drive failure.  

If something catastrophic happens at the location of the redundant drives (power surge, theft, fire, etc), **ALL your data will still be gone**!

---

# 5. Infrastructure

Running your own server or servers requires some thought about infrastructure, but could be as trivial as where to place the hardware.  The questions below are not exhaustive, but are meant to kickstart thinking about infrastructure.

_Network_

* Do you have the required up- and downstream internet speeds to access your data easily?
* Will you be attaching your server with wired ethernet, or wireless?
* Do you need more than one NAT firewall (router) between the internet and your important data?

_Hardware_

* This series of articles will focus on low-powered hardware, but the type of services you plan to run will likely influence this.
* Where will you place the server/s?
* Do you have sufficient cooling, if it is a high powered server (or if it's in an enclosed area)?
* How much storage are you likely to need?

_Power_

* Do you need additional power for extended power outages (UPS vs Generator)?
* What UPS size do you require?
* Have you installed proper lightning protection?
* What will the estimated power use be (and the impact on your power bill)?

_Redundancy_

* Is it acceptable for a server to be down till you can physically attend to it, or do you need failover hardware?
* Do you have storage redundancy in case of drive failure?

---

# 6. Physical (on-premises) servers vs VPS (Virtual Private System)

This is more of a sidenote, but I thought I'd mention it anyway.

While it's entirely possible to run your own server on services like Digital Ocean or CloudAtCost, it does negate some of the benefits mentioned **#2** and **#3** (but also takes care of some other issues like **#5** ).

I would personally recommend only using these services if:

* You're toying with the idea of running your own cloud server and want to experiment first
* The data that you'll be storing is not sensitive in any way
* You do not have reliable internet and power at home

---

# 7. Learn and have fun

With reference to **#1** above, whether you're a seasoned system admin, or just getting started, setting something up that you can actually use, is a useful and fun learning experience.  

Generally, you have to stuff up pretty badly to lose important work (see **#4** ), and rollbacks are part of the learning experience.  

If you're in the position of doing something that somebody else _hasn't_ done yet, and you get it going, the feel-good factor is even higher, and you might even be the one to help someone else with the same issue on a forum somewhere.


_Roelof_