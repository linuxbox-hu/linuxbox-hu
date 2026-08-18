---
author: kecsi
categories:
- debian
created: 1136325221
date: '2006-01-03T00:00:00Z'
title: Hogyan fordíthatunk arhitektúrára optimalizált debian csomagokat.
aliases:
- /node/119/
- /story/119/
---
Az `apt-build` debian csomag segítségével gentoo stílusú architektúrára optimalizált debian csomagokat készíthetünk magunknak.
Telepítsük fel először a csomagot.
```bash
wajig install apt-build
```
közben kérdez bennünk pár opcióról, ezek a `/etc/apt/apt-build.conf` állományba kerülnek lementésre:
```
build-dir = /var/cache/apt-build/build
repository-dir = /var/cache/apt-build/repository
Olevel = -O2
march = -march=pentium4
mcpu = -mcpu=pentium4
options = " "
```
Az elkészült csomagok a `/var/cache/apt-build/repository` könyvtárba kerülnek. Innét aztán egyszerűen telepíthetjük is őket, ha beadjuk a következő sort a `/etc/apt/sources.list` konfigurációs állományunk elejére. (apt-build telepítése közben automatikusan is megtehettük ezt.)

`deb file:/var/cache/apt-build/repository apt-build main`

Továbbá természetesen meg kell adnunk a források elérhetőségét is ugyanitt!

Ha ez is megvan neki is láthatunk csomagokat fordítani miután frissítettük a csomag informacióink!

`sudo apt-build install most`

Amennyiben elkészítjük a /etc/apt/apt-build.list állományt az újrafordítandó csomagok listájával akkor ezeket a csomagokat egyszerre mind is fordíthatjuk.

Például ebből az állományból is kiindulhatunk:
```bash
dpkg --get-selections | awk '{if ($2 == "install") print $1}' \
  > /etc/apt/apt-build.list
```
Ne felejtsük kivenni a gcc és hasonló a művelet elvégzéséhez szükséges csomagot kivenni a listánkból! Ezután már csak:

```bash
sudo apt-build world
```
