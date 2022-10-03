---
layout: post
title: 100DaysOfHomelab 18/100 - Doing the Emby Shuffle
category: 100DaysOfHomelab
tags: homelab virtualization docker container docker-compose media emby
---
### Finally!
So, I finally have a media server set up! I did drop Jellyfin (for now...it really looks like the best thing going if you don't want a subscription) and switched to Emby. It was extraordinarily easy to set up...just copy the docker-config text from the page on Docker Hub. This is another image by linuxserver.io, and it runs great...just like everything from them that I've tried, other than Jellyfin.

----

### Tweaking the Knobs
Most of the day's time has been spent tweaking the server setting, setting up accounts for my family, and organizing media. Currently, I am using a 4TB drive that is connected to my router, and is also where my Calibre library resides. I made a mistake to begin with, and just was storing the files within my WSL instance. I _thought_ that I had set this Windows box up where all "store" apps were stored on D:, which is 8TB. I was incorrect...everything was being stored on C:, which is a 1TB NVME. Needless to say, I ran out of space quite quickly. Until all of that gets moved again across the network, that computer is pretty much out of commission...and I don't have 10GB networking set up yet. So...I guess I'm glad that I write these on my Mac!