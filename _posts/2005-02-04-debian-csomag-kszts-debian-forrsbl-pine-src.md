---
excerpt: "Egy példán keresztül mutatnám be a dolgot:\r\nKészítsük el a jól ismert
  konzolos levelezőprogram a pine legfrissebb csomagját!\r\n\r\nA művelethez szükséges
  apt-get konfigurációban src soroknak lennie!\r\npl.:<strong>\r\ndeb-src ftp://ftp.hu.debian.org/debian/
  sarge main non-free contrib\r\ndeb-src ftp://ftp.hu.debian.org/debian-non-US sarge/non-US
  main contrib non-free\r\n</strong>\r\nLépjünk a src könyvtárba mielőtt letöltenénk
  a forrást.\r\n<strong>cd /usr/src\r\napt-get update\r\napt-get source pine</strong>\r\nElőfordulhat,
  hogy nincs feltelpítve a dpkg-dev csomag a gépünkre, ami a source kicsomagolásához
  kell. \r"
categories:
- debian
layout: story
author: kecsi
title: debian csomag készítés debian forrásból (pine src)
created: 1107510916
---
Egy példán keresztül mutatnám be a dolgot:
Készítsük el a jól ismert konzolos levelezőprogram a pine legfrissebb csomagját!

A művelethez szükséges apt-get konfigurációban src soroknak lennie!
pl.:<strong>
deb-src ftp://ftp.hu.debian.org/debian/ sarge main non-free contrib
deb-src ftp://ftp.hu.debian.org/debian-non-US sarge/non-US main contrib non-free
</strong>
Lépjünk a src könyvtárba mielőtt letöltenénk a forrást.
<strong>cd /usr/src
apt-get update
apt-get source pine</strong>
Előfordulhat, hogy nincs feltelpítve a dpkg-dev csomag a gépünkre, ami a source kicsomagolásához kell. 
Ezesetben: <strong>apt-get install dpkg-dev fakeroot </strong>

Nézzük meg fel van-e telepítve minden függőség:
<strong>apt-get build-dep pine</strong>

Most készítsük el a csomagot(4.62-es verzió a cikk írásokor volt legfrisebb verzió, értelemszerűen ez változni fog.):
<strong>dpkg-source -x pine_4.62-1.dsc
cd pine-4.62
dpkg-buildpackage -rfakeroot -b</strong>

Majd teleíthetjük az elkészült csomagunk!
<strong>cd ..
dpkg -i pine-tracker_4.62-1_all.deb pine-tech-notes_4.62-1_all.deb pine_4.62-1_i386.deb pilot_4.62-1_i386.deb</strong>
