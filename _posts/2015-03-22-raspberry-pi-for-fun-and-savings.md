---
layout: post
title: "Using a Raspberry Pi for fun and savings as a personal cloud server"
date: 2015-03-22 +1000
comments: true
---

This project started as a scratch for a number of small itches:

**_Running my own servers_**

Like any self respecting geek, I like running my own servers to try things out on, and even occasionally use them for doing useful things.

**_I don't trust the cloud (for important things)_**

There, I've said it.  Useful and revolutionary as it is, cloud based servers still have drawbacks that concern me, specifically the fact that I don't really own my data after I've uploaded it into the ether.  This topic is worth a post on its own, so I digress for now.

**_Electricity is expensive_**

Gone are the days where thinking about your electrical bill is a distant afterthought when running computer hardware.  In Queensland, 'normal' residential electricity is now billed at around A$0.27/kWh.  Running a full size headless box (~100W idling), comfortably costs in excess of A$250/year.  Apart from being expensive, it is also a waste of resources, and bad for the environment.

---

Having bought an original Raspberry Pi B (with 256MB RAM) when they first came out, I thought I'd give it a try to see how much I can run on it.  It turns out that the memory ceiling is just a tad too low, so I went and spent a whopping $50 to buy myself a new B+.  Not that the first Pi is going unused, but more on that later.

Using the two Pis and a number of self-hosted packages, I'm in the process of recreating a personal cloud setup that mirrors a number of services I've used for non-critical data, while also addressing the issues mentioned earlier:

* I get to run my own little (cheap) server with useful stuff on it that I can access from anywhere;
* All my data is stored at home (making it easy to backup, and fast to use locally), but available to me via secure channels on the go, just like normal cloud services;
* At 5W, the Pi sips electricity.  Even with an external hard drive attached, it only touches 10W when running balls to the wall.  A side benefit of this is that even a small UPS will keep my server stack going for more than an hour (less of an issue in Queensland, but very useful in places like South Africa right now - thanks Eskom).

How much can I run on a Raspberry Pi, considering it sports somewhat 'limited' hardware compared to modern servers, and still have decent performance?  It turns out, _quite a lot_!  My current (in progress) setup has the following running on my B+ (with average load and memory usage under 50%):

* GitBlit (running under jetty)
* Apache with modPHP, running:
 * Redmine
 * Linux Dash
 * A local ubuntu & debian repository
 * Dokuwiki
* NTP server (based on a Freetronics RTC)
* apt-mirror
* OpenVPN
* rtorrent

On my to-do list are:

* Owncloud
* A mail server
* Wallabag (a pocket clone)
* A download manager
* Datacrow (a library/catalogue application)
* Upsource (repository browsing and code review tool)

---

I will be posting a series of entries on this topic, covering a number of items like security (login credentials, running a VPN, etc), accessibility issues (commandline and web based services) and self hosted services (in areas like general productivity and software development).  Initially, my focus will be on security and productivity, more than sharing or hosting things for other people to see.  However, the latter is certainly possible without compromising the former too much.

Hopefully, it will inspire others to do the same (once they see that it's actually not hard), and I hope to add some value by automating some processes, or making services easier to deploy.

Watch this space!

_Roelof_

