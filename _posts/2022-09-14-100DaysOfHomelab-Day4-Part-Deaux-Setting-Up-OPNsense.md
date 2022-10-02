---
layout: post
title: 100DaysOfHomelab 4/100 Part Deaux - Setting up OPNsense (basic)
category: 100DaysOfHomelab
tags: proxmox homelab virtualization OPNsense firewall router dns ssh certificate
---

## Summary
Setting up OPNsense isn't exactly _easy_ to set up, but it's not overly difficult, either. The UI is phenomenal, and easy to understand. Pro tip: turn on the 'full help' toggle in the upper-right of the details page for configurations. This turns on all of the help text, and makes understanding what the (sometimes strangely named) option is for. Further, the plugin support is great and has lots of different options, all of which come with actual descriptions, instead of just a one-liner.

----

## Updating OPNsense
There are two basic ways to do this:
* In the lobby/dashboard when you log in, there is a link to ```Click to check for updates.``` link. Click it to check for updates immediately
* Alternatively you can navidate there from anywhere in the system by:
	- Click ```System``` from the navigation menu on the left to expand it
	- Click ```Firmware``` to expand it
	- Click ```Updates``` to check for updates
	- In addition, I had an error with the web interface updating.
		+ To fix it, I had to log in via SSH (because the Console in ProxMox _also_ wouldn't connect)
		+ Option 12 in the menu is what it takes to update the server from the console.

----

## Setting up a local CA
After updating, setting up a local CA is the first thing that I do. This is a necessary step for many services in setting up the firewall. After setting up the CA, you'll want to come back here whenever a service requires a certificate, and create it.

Steps:
1. Click ```System``` on the left-hand navigation bar to expand it.
2. Click ```Trust``` to expand it.
3. Click ```Authorities``` to get to the screen where you can add a CA
4. Click the ```+``` in the upper-right hand corner of the page.
	* Give a descriptive name to the server
	* Select ```Create an internal Certificate Authority``` from the dropdown on the Method line
	* Select a Key type on the appropriate line. I chose ```Elliptic Curve```
	* I left the Curve line at prime256v1
	* I changed the Digest Algorithm option to ```SHA512```.
	* I left Lifetime alone (825 days was default for me)
	* The Distinguised Name section should be filled out as much as you like, but enough to identify your server if necessary
	* Click ```Save``` once finished
5. Now you have an internal CA, and can issue certificates from it by selecting ```Certificates``` on the left side
6. Adding a Revocation List can be done from the left side as well.

----

## General Housekeeping
Now is a good time to click through and check that settings were properly applied during the setup wizard, or to fill in anything that you left blank. Going through the navigation menu will also give you a good idea of what services come as standard in OPNsense, and let you start planning what plugins you want to find and set up. Good things to check:
- System
	+ Access
		* Create a new user with a complex password here and store it in a password manager
		* I also add this user to the 'admins' group and check the box to create a user certificate
		* I did also check the box to set up a One Time Password.
			- This was added easily in 1Password (the password manager that I use)
			- I clicked the ```Click to unhide``` button
			- In 1Password, I edited the saved login for OPNsense
			- I added a OTP field
			- I clicked the option to scan a QR code. Older versions required moving a viewfinder around on the screen. This newest version just finds it and adds it automatically.
			- I don't even know if this is usable, or if I need to install another service to use it yet, but we'll see soon enough.
		* I did not create any new servers, though this is where you can add an LDAP or RADIUS server, among others
	+ Configuration
		* Backups
			- This is where you can backup and restore configurations. I'm not ready for this step yet, as I want to get things set up first.
			- Google Drive is also available as an option for backups, if you wish
		* Defaults - Reset the server to default values
	+ Firmware
		* This is where you go to update and to install plugins.
		* Skipping this section for now, as I'll do plugins last, and have already updated
	+ Gateways
		* You should see at least 1 entry here, sometimes 2, depending on if you enabled IPv6
		* The 'WAN_GW' gateway should point to your main router/modem
	+ High Availability
		* This doesn't apply to me right now, as I need more hardware for that, but if you're setting this up as HA, here's where
	+ Settings
		* Administration
			- This is where you can set up how you access the server
			- Selecting the specific certificate you want to use for the site, alternate hostnames, etc.
		* Cron
			- Set up Cron jobs!
		* General
			- Allows you to set up things like the Hostname, the domain, timezone, etc. Most of this should have been set by the wizard
		* Logging / targets
			- This will let you set up a target to send logs to. This will likely be useful once I get around to setting up actual security tooling, like a SIEM
		* Miscellaneous
			- Set up power usage options, hardware acceleration for cryptographic functions, set up periodic backups, etc.
		* Tunables
			- Yeah...no. I am not ready to tackle this page yet! A little too far in the weeds for me so far.
- Interfaces
	+ Check LAN and WAN here to make sure that they are assigned to the correct addresses
	+ I didn't have to change any options, except to prevent the removal of the interface, just to be safe
	+ In Assignments, make sure that you do have the right interface assigned to the right function (LAN/WAN)
	+ I didn't mess with anything else in here, yet
- Firewall
	+ Look through it, I'm not adding anything to this yet, as I'm not ready to actually make this my router.
- VPN
	+ IPsec and OpenVPN are the two default options, though others can be added through plugins
	+ This is one of the main features that I want to get set up and running, but not yet. I want things like a DNS Resolver up and running first.
- Services
	+ This is where a lot of plugins that you install will show up
	+ Intrusion Detection
		* I did turn on Intrusion Detection (IDS), but did not turn on the IPS system, as it would be pointless right now.
		* Enabled syslog alerts
		* Selected both LAN and WAN for interfaces.
	+ Network Time
		* I left this as-is, just making sure that all four opnsense NTP servers were selected
	+ Unbound DNS
		* Unbound DNS is the default service installed in OPNsense to handle DNS serving. I just make sure that this is enabled, and that DNSSEC is enabled.
		* I don't select any of the DHCP options, as I'm not currently using this as a router, and so have DHCP disabled.
		* Checked this on my phone by turning off mobile data, and setting the DNS server for the WiFi network to manual, and entering the IP of OPNsense. It worked with no issues!
		
----

## Closing Thoughts
Setting up OPNsense wasn't that big of a deal. I'm sure it would be (somewhat) more challenging with passed through NICs, but that's not where I'm at right now. Further, plugins will add a great deal of complexity, I am certain, but again, I'm not there yet. I'm not sure what I'll be doing tomorrow, yet, but it might be looking at plugins for OPNsense, or I might set up a different virtualized server.