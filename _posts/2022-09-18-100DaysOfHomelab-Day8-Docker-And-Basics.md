---
layout: post
title: 100DaysOfHomelab 8/100 - Docker and Basics
category: 100DaysOfHomelab
tags: homelab virtualization containers docker heimdall yacht
---
## Summary
So today, given the demise of the ProxMox project for now, I've changed focus. One of the things that I want to get back up and running is a MidPoint container, just to learn on. It's kind of important for the upcoming job start that I'm looking forward to in a couple of weeks. Given that, I wanted to get Docker up and running on my Windows machine, rather than on a virtual server.

This can present some problems, as Windows, well, kind of sucks for running a lot of Docker images that I want to use. The solution (I hope) to this is connecting Docker to my WSL instance. I've done this in the past, in a casual way, and it worked out pretty well.

I've got a few different things that I want to get up and running on Docker, eventually, but the most important ones (short of the MidPoint container) are Heimdall and Yacht. I also want to get Calibre Web Server or COPS up and running, to see if that would be more reliable and/or stable than serving from the Windows PC and connected to a database and files stored on a hard drive plugged in to my router.

----

## Docker
I've gotten Docker Desktop up and running pretty well, and pretty quickly, and it is using the Ubuntu WSL instance on the machine as the backend for Docker itself. Fortunately, Docker makes this pretty easy, and using WSL is now the default behavior for Docker Desktop for Windows.

----

## Heimdall
So Heimdall is basically a landing page for accessing and managing Docker services via a Web UI. It's pretty clean, pretty simple, and well...pretty. Yes, I used that word a lot. Still, it holds true. This was pretty simple to install and get spun up.

----

## Yacht
Yacht, if it does what I want it to (and says it does) will allow me to easily spin up and deploy Docker-based services. This is done via Templates to make things easier. Hopefully, this will greatly simplify spinning up common services that I will want to use, and there are a lot in the basic template repository that I'm wanting to explore

----

## Conclusion
Relatively short post today, but most of it has been in research and reading documentation. Likely, the next several days will be similar, as I try to get Yacht and other services and up and running. After I have everything stable in my base Docker setup, I'll get that MidPoint container set up, and start exploring further services. I'm looking at setting up something like Traffic, something Plex-like for serving media, something to access and read ebooks, a web server, and get started with Kubernetes and likely some sort of orchestration system, maybe Rancher or similar.