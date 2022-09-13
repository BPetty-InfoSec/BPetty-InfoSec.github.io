---
layout: post
title: 100DaysOfHomelab 1/100 - pfSense and OPNsense
category: 100DaysOfHomelab
tags: pfSense OPNsense firewall router homelab virtualization
---
# 100DaysOfHomelab 1/100 #
## pfSense and OPNsense ##

So today marks the "first" day for me of #100DaysOfHomelab. It's the first one that I'm counting, since I just found the idea. So I'll just start where I'm at now.

I have worked for a while homelabbing with virtual machines. Nothing long-term, usually just a project that I'm working on to learn something, with a temporary VM network, using either VMWare Player or VirtualBox. (There was this one time, with libvirt...) Anyway, I started working with pfSense this time to set up a bridge between specific hosts in an otherwise completely segregated virtual network. I was setting up a group of servers as a penetration testing lab, and I wanted to be able to upgrade my Kali install, but didn't want any vulnerable images that I spun up to be accessible to the rest of the network. Took a couple of hours to figure it out, but it ended up working just fine. I had watched some Lawrence Systems videos about pfSense in the past out of curiousity, and remembered one about pfSense vs. OPNsense, so I thought that I'd give OPNsense a try to, which brings us to today.

Both of these are exceptional products, from my brief time with them. That being said, I do like the fact that the community edition of OPNsense gets more updates than pfSense. I mean, if I'm putting up a *firewall* then I expect it to be somewhat secure. Running a significantly older back-end does not fill me with confidence on that front. Still, it's BSD-based, so it's not a complete deal-breaker for me. What really is making me want to stick with OPNsense after trying it today, however, is the layout. I just like it better. Other small quality-of-life things like descriptive information in the plugins page, the ability to toggle on "advanced mode" and "help", and just the larger variety of plugins that seem to be readily available are also swaying me in the direction of working (first) with OPNsense. Now, I'm not saying that pfSense doesn't have those things...but I also don't know if they do or not, and this comes "out of the box" in a better state for me, so that's what I'm going to be going with for now, at least. I'll no doubt change my mind on this, likely numerous times, over the days ahead. For me, that's what homelabbing is all about, anyway...experimentation and learning.

Though I *do* want to keep with the experimentation and learning part of things, I'm also wanting to build out some actual, workable infrastructure for my home network as well. This is sort of the first step to that. I have Comcast as an ISP. That's not necessarily a bad thing, and it's really the only option that I have right now, and don't have too many complaints about it at this point. That said, I want to run my own DNS servers. I want to have access to my home network when away from home (and a VPN for when I'm on hotel wifi). Heck, I want to be able to serve this site in a high-availabilty setup from my house, and tons of other stuff. So homelabbing is something that I've been enjoying getting started in, and something that I've already planned to do for a long time. The 100DaysOfHomelab are more of a way for me to hold myself accountable (though I'm not going to be upset if I miss a day...life happens, and I'll just "make up" the time later) and chronicle my progress for myself.

Next steps: I have an older laptop with 32 gigs of RAM, a terabyte of storage, and an 8 core/16 thread processor. The only downside is the single NIC. Still, I plan on trying to get it set up as a ProxMox server next, and the first thing that will be going on it is OPNsense. If nothing else, it will be my main household DNS server, with fallback to...something else. I've been trying to avoid Google services as much as possible, and CloudFlare has had...issues...lately in the community. Those were my two go-to public DNS servers, so I'll have to do some research on that as well.