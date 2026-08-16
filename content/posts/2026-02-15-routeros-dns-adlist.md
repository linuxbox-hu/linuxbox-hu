---
author: kecsi
categories:
- site
date: '2026-02-15T19:44:52Z'
image:
  path: static/assets/img/logos/MikroTik-logo-2021.png
tags:
- MikroTik
- RouterOS
- adlist
title: MicroTik RouterOS DNS adlist
---
![MikroTik](/assets/img/logos/MikroTik-logo-2021.png)

Ha a routerunk tamogatja a DNS adlist-ek hasznalatat akkor ennek beallitasaval egyszeruen megszabadulhatunk a belso halozatunkon a reklamoktol.
Azaz nem feltetlen van szuksegunk egy kulon Pi-Hole DNS fekete lista szolgaltatas futtatasra. Igaz a router adlist nem ad latvanyos statisztikakat es nem rajzol beloluk diagramokat de azt hiszem ezek nelkul meg lehet elni...

> Fontos: ne feledjuk a DNS cache maximalis meretet megnovelni ha beadunk egy nagyobb adlist-at.

Hasznos linkek a temaban:

* [Why Pi-hole when you can RouterOS adlist?](https://www.youtube.com/watch?v=RMJnjyAOfLI)
* [MicroTik Docs - DNS - Adlist](https://help.mikrotik.com/docs/spaces/ROS/pages/37748767/DNS#DNS-Adlist)
* [GitHub - StevenBlack - hosts](https://raw.githubusercontent.com/StevenBlack/hosts/refs/heads/master/hosts)

