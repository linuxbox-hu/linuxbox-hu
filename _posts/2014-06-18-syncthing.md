---
layout: post
title: Syncthing
date: 2014-06-18
author: szimszon
categories: [linux]
tags: Syncthing
excerpt: Syncthing egy multi platformos, nyílt kódú fájl szinkronizáló megoldás BTSync  helyett.
---
[Syncthing](http://syncthing.net/) multi platformos, [nyílt kódú](https://github.com/calmh/syncthing/blob/master/protocol/PROTOCOL.md) fájl szinkronizáló megoldás [BTSync](http://www.bittorrent.com/sync) helyett.

![Syncthing screenshot](http://syncthing.net/screenshot.png)

A fejlesztő [elmondása](https://discourse.syncthing.net/t/security-principles/48) szerint biztonság és az adatok védelme az elsődleges cél.

Jelenleg még nem tart az 1-es verziónál, de ígéretes sebességben megy a [fejlesztés](https://discourse.syncthing.net/t/release-schedule/45).

Az alábbi rendszereken futtatható:

- Mac
- Windows
- Linux
- BSD
- Solaris

A programot [Go](http://golang.org/)-ban írják és a fejlesztés a [Github](http://github.com/calmh/syncthing)-on van. A kezelői felülete weblap.

Működését tekintve a gépek közötti kapcsolatot [TLS](https://en.wikipedia.org/wiki/Transport_Layer_Security)-sel titkosítja. A [gépek (node) egyéni azonosítót kapnak](https://discourse.syncthing.net/t/how-node-ids-work/365), egy 52 karakteres kódot amik azonosítják a hálózaton. Helyi hálózaton belül üzenetszórással (UDP 21025-ös port) értesítik elérhetőségükről a kliensek egymást. Egyéb esetben IP, gépnév (DNS) vagy bekapcsolható a „global discovery”, amikor a „global discovery service”-re a node ID és a külső port elérés beregisztrálásra kerül, ami lekérdezhető, találják meg egymást a gépek. A [tűzfal](https://discourse.syncthing.net/t/firewalls-and-port-forwards/166/3) (TCP 22000-ös port) beállításában az [UPnP](https://en.wikipedia.org/wiki/Universal_Plug_and_Play) segít.

Jelenleg 1 millió fájl lehet egy kötetben és egy fájl kb. max. 12GiB lehet. Valamint egyenlőre a fájl index a memóriában tárolódik. Ld.: [GYIK](https://discourse.syncthing.net/t/frequently-asked-questions-faq/405)

Indulásnak érdemes elolvasni a „[Getting Started](https://discourse.syncthing.net/t/getting-started/46)” leírást.

Amit érdemes észben tartani, hogy minden gépen minden klienst fel kell venni kézzel és a szinkronizálandó köteteket egyező ID-val fel kell venni mindenhol.

[Beszélgetések](http://discourse.syncthing.net/) :: [Leírások](http://discourse.syncthing.net/category/documentation) :: [Letöltések](https://github.com/calmh/syncthing/releases/latest) :: [Fejlesztés](http://github.com/calmh/syncthing)
