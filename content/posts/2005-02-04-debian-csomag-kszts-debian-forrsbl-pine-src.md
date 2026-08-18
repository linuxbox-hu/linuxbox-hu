---
author: kecsi
categories:
- debian
created: 1107510916
date: '2005-02-04T00:00:00Z'
title: debian csomag készítés debian forrásból (pine src)
aliases:
- /node/17/
- /story/17/
---
Egy példán keresztül mutatnám be a dolgot:
Készítsük el a jól ismert konzolos levelezőprogram a pine legfrissebb csomagját!

A művelethez szükséges apt-get konfigurációban src soroknak lennie!
pl.:```
deb-src ftp://ftp.hu.debian.org/debian/ sarge main non-free contrib
deb-src ftp://ftp.hu.debian.org/debian-non-US sarge/non-US main contrib non-free
```text
Lépjünk a src könyvtárba mielőtt letöltenénk a forrást.
```bash
cd /usr/src
apt-get update
apt-get source pine
```
Előfordulhat, hogy nincs feltelpítve a dpkg-dev csomag a gépünkre, ami a source kicsomagolásához kell. 
Ezesetben: `apt-get install dpkg-dev fakeroot `

Nézzük meg fel van-e telepítve minden függőség:
`apt-get build-dep pine`

Most készítsük el a csomagot(4.62-es verzió a cikk írásokor volt legfrisebb verzió, értelemszerűen ez változni fog.):
```bash
dpkg-source -x pine_4.62-1.dsc
cd pine-4.62
dpkg-buildpackage -rfakeroot -b
```

Majd teleíthetjük az elkészült csomagunk!
```bash
cd ..
dpkg -i pine-tracker_4.62-1_all.deb pine-tech-notes_4.62-1_all.deb pine_4.62-1_i386.deb pilot_4.62-1_i386.deb
```
