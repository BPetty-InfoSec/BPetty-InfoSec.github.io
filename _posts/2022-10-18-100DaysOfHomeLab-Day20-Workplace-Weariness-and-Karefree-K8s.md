---
layout: post
title: 100DaysOfHomelab 20/100 - Workplace Weariness and Karefree K8s
category: 100DaysOfHomelab
tags: homelab virtualization docker container docker-compose kubernetes k8s k3s
---
Well, as I've mentioned a few times previously, I have a new job. I'm out of training, and that's great, I really love what I do (entry-level IAM Engineer), and it's certianly interesting! Unfortunately, as the learning curve is pretty steep, it leaves me a bit "brain dead" at the end of the day. Totally worth it! Also, totally a buzzkill for the whole #100DaysofHomeLab challenge. Still, I'm not giving up in any way, I'm still excited to be working on this! It does mean, however, that I may be posting about once a week for the next month or two (or three...). So things will be a bit slower than I'd like, but I still have to take time for stuff around the house, my family, and frankly my mental health. I'm not a kid, and I've been working a long time...I've already made all of those mistakes, and I'm not interested in making them again. I'm not interested in making them again.

----

My next move (and I have been poking at this behind the scenes, at least every other day, just not enough to write about) is to transition from Docker containers run by themselves, and then via Docker-Compose, to finally take the plunge into Kubernetes. I'm leaning towards K3S right now. The Rancher people seem pretty responsive, and it's fairly well documented. The eventual goal is to connect my internal network to the outside internet via a loadbalancer. I'd like to set up virtual docker networks to keep some segmentation, and make it so that only the services that I want to be available to me (and friends) are exposed, with my internal services only available remotely via VPN, just for that extra layer of seperation. This is what I'm looking at:

![HomeLab Architecture](/img/HomelabArchitecture.png)
_Proposed Homelab Architecture_
