---
layout: post
title: 100DaysOfHomelab 17/100 - Jellyfin Stings
category: 100DaysOfHomelab
tags: homelab virtualization docker container docker-compose frustration jellyfin permissions
---
So today, there is Jellyfin. Well, there is a container that has Jellyfin in it, but I can't really access it. This is frustrating on several levels. The issue is permissions. I just deleted a long rant about linuxserver.io and their incomprehensible decision to utterly override user choice on permissions for the ```/config``` directory in the image. I tried a different image with another image (```jellyfin/jellyfin```) but it had other issues. Frankly, I'm sick of it. I'll probably go back to using Plex unless someone has an idea to make it work correctly. The issues on the GitHub page were...well, frankly, they were completely unhelpful, with overbearing and rude contributors. Seriously reconsidering ever using anything else from linuxserver.io. I'm not a big fan of condescension.

----

So I wrestled with this for several hours, to no avail. Given that, I'll be dropping the Jellyfin part of this project for now. Hopefully, as I continue to learn, I'll be able to come back to it and get it working in the near future. That being said, I tried Emby just on a lark...it set up without issue, using the instructions from Docker Hub. No issues at all so far. This is also an image from linuxserver.io, which leads me to believe that the real issue here was Jellyfin. Who knows?