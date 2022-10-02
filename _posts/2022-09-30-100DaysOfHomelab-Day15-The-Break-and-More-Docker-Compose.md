---
layout: post
title: 100DaysOfHomelab 15/100 - The Break and More Docker Compose
category: 100DaysOfHomelab
tags: homelab virtualization docker container docker-compose
---
So if you're one of the (maybe 1-2) people who follow me blogging here, then you probably have noticed that I haven't posted in a week. Well, I started a new job on Monday. Frankly, after getting off of work each day, I had plenty of time to work on things...I just didn't have the mental bandwidth! Training is always a lot of fun, but it can be kind of draining, mentally speaking. So I finished today, and (since I've got a couple of days off in front of me), I picked back up working in Docker.

Mostly today is simply working on updating my docker-compose file and attempting to get Calibre to recognize the volume with all of my books in it. The actual directory that the books are in are on a hard drive connected to my router, which I can access via SMB. So to try and make this work, I have mounted the samba share to the directory that I wish to use as the volume. The problem is...it's not working. I need to investigate and see if this is something that is normal in Docker, and I need to do a different workaround, or if I'm simply declaring the volume incorrectly. I may mess around with a PostgreSQL container, since I would also want to mount a volume for it, and it's a little more straightforward than something like Calibre.