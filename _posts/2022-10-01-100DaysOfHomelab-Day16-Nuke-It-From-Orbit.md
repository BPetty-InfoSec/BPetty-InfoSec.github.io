---
layout: post
title: 100DaysOfHomelab 16/100 - Nuke It From Orbit
category: 100DaysOfHomelab
tags: homelab virtualization docker container docker-compose frustration
---
Hello again! Maybe "Hello World" might be appropriate, here. As you can probably tell from the title, today's exercise in futility with Docker finally got to the point where I tore it all down. I deleted all of the volumes, I deleted all of the images, and I even deleted everything out of my ```docker-compose``` file and started over.

I am pleased to announce that as of now, _almost_ everything is working! Heimdall is up and running without issue, and now has a linked volume so that I don't have to re-pin services every time I take down the container. PostgreSQL is up and running without issue, and connection via PGadmin has been seemless. I even got Redis up and running, along with Redis Commander, all working well. Both databases have their own volumes for persistence.

I did create some media folders on the shared drive on my network, and mounted them locally. I'm attempting to put up Jellyfin, to allow media sharing, etc. So far, this is the only service that isn't up and working normally, but I'm not frustrated. It's late enough that tonight is now tomorrow, and I've got a good start. So poking at Jellyfin (it appears to be a permissions issue, which I really need to learn about with Docker anyway) is the first order of business tomorrow, once I get into the homelab.

Also, welcome to Cybersecurity Awareness Month! As a PSA: _do not_ refer to Cybersecurity Awareness Month as CSAM. That is an acronym that already means something, and it's something that none of us want to be associated with...well, at least I hope so. If you do, please no longer read this blog, and remove me from any social media where you may be following me because...ew. All that being said, once I get Jellyfin up and working, then I'll be turning my attention to more security-focused projects. A to-do list:

**To Do for Cybersecurity Awareness Month**
* Set up a load balancer (optional, but preferable)
* Set up a VPN for access when away from home
* Set up Grafana services and get them integrated
	- Grafana (um, duh)
	- Loki
	- Prometheus
	- (Maybe more, I don't know yet)
	- See if Grafana can be made into something like a SIEM, or if there is an app that is a SIEM that integrates with it
* Set up Traefik to serve web pages with automated LetsEncrypt updates for https support
* If ALL of that is done, or as done as I'm happy with, then I'll go back to attempting to set up Calibre in a container.
	- This is an add-on because I already have Calibre running locally with the library on a network drive.
	- Ironically, Calibre is running on the box that I run Docker on...so the IP address for the server won't even change
		+ Waiiiiiit a minute, that's something to consider: stopping the Calibre server before trying to start the container with a conflicting port...