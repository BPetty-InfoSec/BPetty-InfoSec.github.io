---
layout: post
title: 100DaysOfHomelab 4/100 - ProxMox...Finally!
category: 100DaysOfHomelab
tags: proxmox homelab virtualization
---
## Summary
Finally I'm getting to installing ProxMox. This has...not been a seamless process! I had a couple of problems right out of the gate:
1. I didn't have an ethernet cable, and ProxMox does _not_ include the tools necessary to connect to WiFi out of the box
2. ProxMox _really_ wants you to buy their subscription. So much so that the non-subscription repository is not enabled by default, but the enterprise repo (requiring a subscription) _is_. This could be so easily avoided by simply giving the user the choice (with the warning message) that non-subscription versions are not safe for a production environment. This is vehemently opposed by ProxMox staff in their forums, however. Great software. Great support, even. Terrible attitude towards the community.
3. When trying to connect to the web interface, I got a blank screen.

----

## Fixes
**No ethernet cable:** I stole the one from my desktop Windows PC temporarily.

**Subscription:** This was simple enough, once I figured out what was going on.
* You first edit the ```/etc/apt/sources.list.d/pve-enterprise.list``` file in the text editor of your choice. Comment out the single line in this file, then save and exit.
* Next, edit the ```/etc/apt/sources.list``` file in the text editor of your choice. Add this line to the bottom:
	- ```deb http://download.proxmox.com/debian/pve bullseye pve-no-subscription``` then save and exit.
* Now, you can ```apt update``` and ```apt upgrade``` without errors.
* Instructions for this can be found in the [ProxMox Wiki](https://pve.proxmox.com/wiki/Package_Repositories)

**Blank Screen on the Web Interface or No Response:**
* First, make sure that you're connecting to ```https://[your_proxmox_ip]:8006```. The https part is critical, as http will fail.
* If that didn't work, try a different browser or a private window (or clear your cache)
* Next, if that didn't fix the problem, then you'll need to log in to the server as root.
	- This can be done on the physical machine (I used a laptop, so this was pretty easy for me), or you can ssh to ```root@[your_proxmox_ip```. Login is `root` and the password will be what you set during installation.
* Follow the instructions in the [ProxMox Forums](https://forum.proxmox.com/threads/blank-web-interface.81356/)
	- You might try restarting the services with ```systemctl restart [services_starting_with_'pve']```
	- Main thing that might work is reinstalling some packages that deal with the web frontend.
		+ Run ```apt install --reinstall pve-manager``` as root and check to see if it worked
		+ Run ```apt install --reinstall proxmox-widget-toolkit``` as root and check to see if it worked

My particular situation required using a private window. It still does, don't know why, but at least I can access it!

----

## Setting Up
Great setting up instructions video here: [Techno Tim - Virtualize Ubuntu Server with ProxMox VE](https://www.youtube.com/watch?v=YR9SNDD8WB4)
This video uses an older version of ProxMox than current, and an older version of Ubuntu Server (it's from 2020) but the basic instructions still work. I'm working through this as I type this post, so if I see anything major that has changed and I have to figure out, I'll note it below.
1. Upload the ISOs that you need to your local ([server_name]) storage.
	- Just expand your server (under 'Data Center' on the left hand side)
	- Select the local storage
	- Click the 'Upload' button to upload from local storage, or click 'Download from URL' and paste in the URL for the ISO
		+ I had to do OPNsense from my local computer, as it downloads as a .bz2, and I had to decompress it first
2. Right click on the node that you have, and select 'Create VM'
	- Go ahead and configure Memory Ballooning during setup
	- If you're installing (as I was) OPNsense or something similar, be sure to add a Network Interface from the Hardware tab for the VM before you boot it up. I didn't, and had to restart, but that's not such a big deal.
	- The Console tab lets you access your VM from the web interface, without needing to directly SSH in
3. Start your VM, and install the OS as usual.

----

## Installing OPNsense
This is pretty straightforward.
1. Make sure that the ISO you downloaded from the [OPNsense Download Page](https://opnsense.org/download/) is the 'DVD' image type
2. When it boots up, _don't_ log in with root.
	- Login: ```installer```
	- Password: ```opnsense```
3. Select the options that you want, I do recommend going ahead and changing the root password to something better.
4. Once everything is installed, reboot
5. From there, log in as root (using either ```opnsense``` as the password, or the new password you set)
6. Make sure that the interfaces (there should be two) are both showing up. If not, select option 1 to assign interfaces to WAN and LAN
7. Assign the interfaces if there is a specific IP address that you want to use, or if they are on the wrong subnet.
8. From there, you should be able to connect to the web interface for OPNsense!
9. Run through the setup wizard 
	- Make sure to _UNCHECK_ 'Block RFC1918 Private Networks' when configuring the WAN interface, as otherwise your router/firewall won't accept incoming connections from your home network!
10. From here, just install any packages that you want to and/or set any configurations that you want.