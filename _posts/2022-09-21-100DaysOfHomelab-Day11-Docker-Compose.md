---
layout: post
title: 100DaysOfHomelab 11/100 - Docker Compose
category: 100DaysOfHomelab
tags: homelab virtualization containers docker docker-compose
---
## Summary
So, this is a day where I'm looking up a lot of things and trying to set some infrastructure up via Docker. In my research and planning, I found out that I need (like, really, _really_ need) to learn Docker Compose. So, I've set up a private GitHub repo to hold some yaml. The way that I've got it set up right now, I've got a directory that contains my general services that I'm usually going to want to be up, called Wyrmhole. I've got another folder with it's own docker-compose file called HackingLab. Eventually, this will be a Kali container (the only one in there right now) as well as several vulnerable machines or other infrastructure. I plan to put this into it's own, isolated subnet.

----

## Networking and Subnets
Speaking of docker networking and subnets, this is one of the problems that I'm having right now. I want to use ipvlan L3, as L3 networking is just...easier and cleaner, honestly. _BUT_ that's not working right now. While the network is still in my compose file, it's commented out at this point. Everything creates and spins up without issue, but I can't access any of the services...and they can't access anything outside of the docker network. I do have a static route set up on my router leading to the host computer, and specifying the /24 networks that I was setting up. I was going to have (in the primary compose file) a separate network for general services, one for Grafana-related services, and one for "business" related containers, generally things that I spin up to be able to learn/train on. Right now, I'm in port-tracking hell, trying to keep up with 1-2 ports exposed for something like 7 containers.

----

## Current Containers (Proposed)
So the current set of containers that I'm looking at having (right now) available all/most of the time:

### General
* Heimdall
* Yacht
* PostgreSQL
* Redis
* Calibre
* Traefik
### Log and Info on the Network
* Grafana
* Loki
* Prometheus
### "Business" containers
* MidPoint

----

## Current Status
This is the list of what I'm working on getting up and running in my primary docker-compose file...and it's definitely a work in progress. Of all of this: MidPoint and Heimdall are working, lol. Yacht _was_ working, but with the docker-compose, it...isn't. Not sure why yet Still, MidPoint was the one that I wanted to work the most. I'm still having issues with volumes and mounting them. Calibre, for example, works fine. _EXCEPT_ that it doesn't mount the volume to the correct place. The directory is created, but it's initialized as an empty directory, with just the default db and default "book" on how to use Calibre. This is the current part of the docker-compose.yaml file dealing with Calibre:
```{yaml}
  calibre:
    image: linuxserver/calibre:latest
    container_name: calibre
    ports:
      - "8090:8080"
      - "8091:8081"
    restart: always
    environment:
      - PUID=1000
      - PGID=1000
      - TZ=America/Indiana/Indianapolis
    volumes:
      - ./calibre-lib:/config
}
```

Any suggestions? Email me at brian@bpetty.tech, or DM me on Twitter (@matrixwyrm)