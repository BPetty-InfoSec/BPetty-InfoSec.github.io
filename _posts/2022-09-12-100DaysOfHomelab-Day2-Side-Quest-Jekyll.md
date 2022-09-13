---
layout: post
title: 100DaysOfHomelab 2/100 - Side Quest - Jekyll
category: 100DaysOfHomelab
tags: jekyll homelab website blog
---

# Side Quest: Jekyll

So yesterday, the goal for today was to set up ProxMox on an old laptop that I have sitting around. That's still on the agenda, but this is a "SQUIRREL!" moment for me. I wanted to set up a blog page/site for my homelab journey. So, I used Chirpy as a template on GitHub (https://github.com/cotes2020/chirpy-starter), like the one used by @TechnoTim in his documentation site (https://docs.technotim.live/posts/jekyll-docs-site/). I wanted basically the same things, such as a dark theme and some of the customizations. While sure, I like to build everything from scratch as a learning experience, I'm not a front-end dev. I like using templates where possible for web pages and sites. I even thought about using WordPress or something like that, but WordPress has a _ton_ of vulnerabilities if it's not set up juuuuuust right. I am not that person at this point in time, and so I wanted to use a static site generator. Since I found the idea for #100DaysOfHomelab from @TechnoTim, I looked through their videos on YouTube and found his tutorial for Jekyll, which you can see from the link to their docs page above.

This isn't done yet. As a matter of fact, this page can't even be read right now outside of my machine (it DOES work on my machine!) because I have to sort out some SSL stuff with Cloudflare and GitHub to get it set up on Pages. Eventually, I'd like to take this back to my homelab, once I have a stable environment, and host it from there.
> The https site is now live, fixed the DNS error that was causing it to fail. <a href="https://bpetty.tech">https://bpetty.tech</a> if you are on the standard http site.
{: .prompt-info }

### Things to happen before that:
- Stable ProxMox server running on bare metal (No VM for this one)
- OPNsense firewall/router stable
- A load balancer: either for OPNsense using HAProxy or a Kemp load balancer...or something else that I haven't seen yet
	+ An SSL cert for the load balancer NOT from a self-hosted CA
- Another stable (virtualized) server for me to host it on
	+ Alternatively, a High-Availability container cluster (Rancher, maybe) to provide failover and scale, as much as I can with my home internet bandwidth

It's going to be a fun ride. I may actually get to the ProxMox server tonight, at least the base install, but there are (unfortunately!) other things to do.