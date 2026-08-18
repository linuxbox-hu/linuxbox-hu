---
author: Goosfrabaa
categories:
- linux
created: 1360156644
date: '2013-02-06T00:00:00Z'
description: |
  Amennyiben VirtualBoxban létrehozott fájlrendszereinket közvetlenül akarjuk elérni (azaz mountolni), egyszerű parancssori alkalmazással megtehetjük azt.
title: VirtualBox meghajtók (VDI, VMDK, VHD stb) direkt elérése
aliases:
- /node/849/
- /story/849/
---
Amennyiben VirtualBoxban létrehozott fájlrendszereinket közvetlenül akarjuk elérni (azaz mountolni), egyszerű parancssori alkalmazással megtehetjük azt.
<!--break-->
Figyelem! Az itt bemutatásra kerülő megoldást célszerű kikapcsolt állapotú (azaz fájlrendszert nem használó) virtuális gép mellett kell végezni, hogy elkerüljük az adatvesztést.
<ul>
<li>Először is telepíteni kell a `virtualbox-fuse` (vagy `vdfuse`) csomagot. Fontos, hogy a `/etc/fuse.conf` fájlban aktiváljuk a *user_allow_other opciót*.</li>
<li>Ezt követően először is 'láthatóvá tesszük' a virtuális image fájl szerkezetét (a partíciókat):
`vdfuse -f /utvonal/file.vdi /celkonyvtar/`</li>
<li>Egyetlen partíció esetén a `/celkonyvtar/Partition1` fájl lesz az, amit konkrétan fel tudunk csatolni (rootként!):
`mount /celkonyvtar/Partition1 /masik_celkonyvtar`</li>
<li>A felmountolt meghajtók leválasztása:
`umount /masik_celkonyvtar`
`fusermount -u /celkonyvtar`</li>
</ul>
