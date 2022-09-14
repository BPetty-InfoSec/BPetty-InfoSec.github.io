---
layout: post
title: 100DaysOfHomelab 3/100 - More Sidequesting
category: 100DaysOfHomelab
tags: jekyll homelab website blog
---

### Blog update
Well, Jekyll and Chirpy together look great, and so far it is great! That being said, there are some...quirks...with how the posts and tabs work, especially with the test server.

Some of these quirks:
1. Show favicons
2. Show new tabs
3. When adding a new tab, the local build breaks. Now, when I build it on my machine it just puts the images in the root folder (_site/) and doesn't serve anything but an index to that directory. I have to push to GitHub and use it's Jekyll Build action to see the results of changes
4. Horizontal rules are weird. Sometimes they work. Sometimes, they comment out the code.

Most of today has been spent updating my blog site to include my resume, and formatting that somewhat. I'll be working on that for the rest of today, likely. Next steps is to try using HTML to center some content on the resume so that it isn't _all_ left-justified. That's great for a normal blog post, like this one, but not so good for a resume.

----
### ProxMox...when?
I'm enjoying this blog quite a bit, as well as working on the homelab. I took today to work on it as I realized something fairly important as I was getting ready to install ProxMox on my old laptop: I don't have a network cable. Total facepalm moment. I may still do the install tonight, but likely won't have it up and running until tomorrow at the earliest.

----
### Future projects
What does the future hold? Well, that's a pretty big question, and there's lots of stuff that I want to do.
* A load balancer for the network
	- I'm considering either a free/community Kemp load balancer, or just using haproxy on the firewall
* A development server
	- Developing on a Mac is pretty nice. Developing on Windows is...meh. I'd really like to spin up a usable VM that I can develop on
* VPN access
	- I'm not terribly interested in an always-on VPN...it's just not necessary for most things.
	- I _do_ want to have a VPN available to me that will allow me to (more) safely use public WiFi.
	- I run a local [Calibre](https://calibre-ebook.com/) server for all of my ebooks. We have a..._**lot**_ of ebooks.
		+ Just as an example, when my wife and I first moved to Indiana, we were living for a time with her mom, until we found our own place. We didn't have space there to store all of our stuff, so we stored it in a spare bedroom at her dad's. It was a little while until we tried to get our stuff out of there (_lots_ of weird conincidental things derailing that) and it turned out that the roof over that room leaked. I lost over a thousand paperbacks due to water and mold damage. We have more ebooks than that, easily.
		+ Did you know that [Paizo](https://paizo.com/) sells pdf copies of their rulebooks cheaper, and that they're often in [Humble Bundles](https://www.humblebundle.com/)?
* A server to...serve stuff 
	- I already have the storage for the above-mentioned Calibre server on a drive attached to my current router, but I'd like to use that for backups, and have the actual server running on its own VM.
	- Currently, the Calibre app resides on my Windows desktop, as it has plenty of processing power and memory to handle it. I'd just like to offload and virtualize it.
* Containers!
	- I'm specifically interested in setting up scalable and resilient clusters.
* High Availability
	- We're getting pretty far in the future here, but eventually I'd like to have enough physical machines to set up high availability services.
	- OPNsense will be the first thing that I try to do this with, as it will be serving (hopefully by this point) as my router, firewall, VPN, and DNS server
	- Then, on to serving a Kubernetes (or other, as something new might come out by then) cluster in HA mode.
		+ Maybe Rancher? There are at least some decent tutorials on that one out there.
* Home Automation
	- By the time we get to this point, Matter will likely be out. Maybe. Someday.
	- I'm hoping to utilize something like [Homebridge](https://homebridge.io/) if it hasn't come out widely, or if it isn't all that it's cracked up to be.
	- I do prefer using Apple's Homekit devices where possible, as they do offer better security out of the box in most cases (be careful, though, as not all do!)
* Local CI/CD pipeline
	- I really want to get this going, probably sooner than where I have it in the list here.
	- DevOps/DevSecOps is something that I'm interested in, but haven't really worked with hardly at all.
* Game servers
	- My son likes Minecraft.
	- I like to build things in games.
* Cacheing content server for Steam?
	- Not sure about this one, but it would be handy if I could build a box with enough storage to make it usable and feasible.
* Self-Hosting this site
	- Again something that I probably should have put in earlier.
	- I'd like for the bpetty.tech domain to just point to my home network.
	- Yes, there's going to be plenty of segmentation, firewalls, hardening, and such before I do this and open it to the public.
	- This will likely be right after I figure out the CI/CD pipeline, as I really appreciate the code checks and automatic build when I push changes to this site on GitHub
* Local git server
	- I mean...why not?
* Actual physical improvements
	- A rack
	- Actual servers
* NAS or SAN
	- I'm looking at setting up a server with a large amount of storage at some point
	- This would partially be used for backups and snapshots, but also for regular files.
	- If I have access to the home network remotely, then I wouldn't necessarily need as much storage on mobile devices
* Plex
	- I have _stacks_ of DVDs. My wife loves movies, I like several series.
	- I'd love to have this set up so that I can stream both locally and remotely.
		+ Storage and compute have to be there for this, though, so right now it's not happening
* Experiments!
	- This is one of the main reasons that I want to do homelabbing.
	- I'm always interested in trying out new applications, and when I have the money I like to play with hardware.
	- Given that, experimentation is going to be a big theme for me once I have the basic infrastructure set up.