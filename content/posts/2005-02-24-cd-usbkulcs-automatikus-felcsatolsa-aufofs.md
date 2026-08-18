---
author: kecsi
categories:
- debian
created: 1109271135
date: '2005-02-24T00:00:00Z'
excerpt: |
  Az autofs egy a linux  kernel által natívan támogatott fájlrendszer. Segítségével a cserélhető meghajtóinkat könnyedén kézi csatolás nélkül elérhetjük.
  
  Nézzük hogyan is lehet elérni ezt pl. egy debian rendszeren.
title: CD, USBKulcs automatikus felcsatolása; AufoFS
aliases:
- /node/34/
- /story/34/
---
Az autofs egy a linux  kernel által natívan támogatott fájlrendszer. Segítségével a cserélhető meghajtóinkat könnyedén kézi csatolás nélkül elérhetjük.

Nézzük hogyan is lehet elérni ezt pl. egy debian rendszeren.
<!--break--> 
Először is legyen legalább modulba befordítva a kernelünkbe az AUTOFS támogatás. (Ha az alap debian kernelt használjuk akkor ez természetesen megvan.)
Pl. Így győződhetünk meg h rendben van-e ez:

linuxbox:~>```bash
grep AUTOFS /boot/config-2.6.8-2-686
CONFIG_AUTOFS_FS=m
CONFIG_AUTOFS4_FS=m
```text
Telepítsük fel az autofs csomagot

linuxbox:~>`apt-get install autofs`
Figyeljünk a verzió legyen 4.1.3, vagy újabb.

Majd konfiguráljuk most a csomagot:
Kedvenc szerkesztőnkkel nézzünk bele a `/etc/auto.master` állományba.

A következő sor 
`/media  /etc/auto.media --ghost --timeout=1`
a media alkönyvtár alá fog inditani egy autofs démont, ami további konfigurációval azaz `/etc/auto.media` állományban megadott eszközöket automatikusan fogja kezelni egy-egy alkönyvtárban.

Az `/etc/auto.media` állomany nálam igy néz ki:
```
cdrom           -fstype=iso9660,ro,nodev                       :/dev/scd1
cdwriter        -fstype=iso9660,ro,nodev                       :/dev/scd0
pendrive        -fstype=vfat,rw,uid=1000,gid=1000,umask=002    :/dev/sda1
```text

Végül már csak három tennivalónk maradt:
`/etc/default/autofs` állományban kisebb `TIMEOUT=1` értéket állítsunk, készítsük el a gyökér könyvtárát `mkdir /media`
 majd íjraindítani a 
`/etc/init.d/autofs restart`
bekonfigurált szoftvert.

Kellemes hekkelést kívánok!

ui: Az eredeti <a href="http://www.desktop-linux.net/autofs.htm">cikket angolul</a> itt találtam.
