---
excerpt: "Amennyiben VirtualBoxban létrehozott fájlrendszereinket közvetlenül akarjuk
  elérni (azaz mountolni), egyszerű parancssori alkalmazással megtehetjük azt.\r\n"
categories:
- linux
layout: story
author: Goosfrabaa
mail: gabrea@freemail.hu
title: VirtualBox meghajtók (VDI, VMDK, VHD stb) direkt elérése
created: 1360156644
---
Amennyiben VirtualBoxban létrehozott fájlrendszereinket közvetlenül akarjuk elérni (azaz mountolni), egyszerű parancssori alkalmazással megtehetjük azt.
<!--break-->
Figyelem! Az itt bemutatásra kerülő megoldást célszerű kikapcsolt állapotú (azaz fájlrendszert nem használó) virtuális gép mellett kell végezni, hogy elkerüljük az adatvesztést.
<ul>
<li>Először is telepíteni kell a <em>virtualbox-fuse</em> (vagy <em>vdfuse</em>) csomagot. Fontos, hogy a <em>/etc/fuse.conf</em> fájlban aktiváljuk a <em>user_allow_other opciót</em>.</li>
<li>Ezt követően először is 'láthatóvá tesszük' a virtuális image fájl szerkezetét (a partíciókat):
<strong>vdfuse -f /utvonal/file.vdi /celkonyvtar/</strong></li>
<li>Egyetlen partíció esetén a <em>/celkonyvtar/Partition1</em> fájl lesz az, amit konkrétan fel tudunk csatolni (rootként!):
<strong>mount /celkonyvtar/Partition1 /masik_celkonyvtar</strong></li>
<li>A felmountolt meghajtók leválasztása:
<strong>umount /masik_celkonyvtar</strong>
<strong>fusermount -u /celkonyvtar</strong></li>
</ul>
