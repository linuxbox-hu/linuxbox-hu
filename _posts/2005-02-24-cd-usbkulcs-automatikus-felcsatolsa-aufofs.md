---
excerpt: "Az autofs egy a linux  kernel által natívan támogatott fájlrendszer. Segítségével
  a cserélhető meghajtóinkat könnyedén kézi csatolás nélkül elérhetjük.\r\n\r\nNézzük
  hogyan is lehet elérni ezt pl. egy debian rendszeren.\r\n"
categories:
- debian
layout: story
author: kecsi
title: CD, USBKulcs automatikus felcsatolása; AufoFS
created: 1109271135
---
Az autofs egy a linux  kernel által natívan támogatott fájlrendszer. Segítségével a cserélhető meghajtóinkat könnyedén kézi csatolás nélkül elérhetjük.

Nézzük hogyan is lehet elérni ezt pl. egy debian rendszeren.
<!--break--> 
Először is legyen legalább modulba befordítva a kernelünkbe az AUTOFS támogatás. (Ha az alap debian kernelt használjuk akkor ez természetesen megvan.)
Pl. Így győződhetünk meg h rendben van-e ez:

linuxbox:~><strong>grep AUTOFS /boot/config-2.6.8-2-686 
CONFIG_AUTOFS_FS=m
CONFIG_AUTOFS4_FS=m
</strong>
Telepítsük fel az autofs csomagot

linuxbox:~><strong>apt-get install autofs</strong>
Figyeljünk a verzió legyen 4.1.3, vagy újabb.

Majd konfiguráljuk most a csomagot:
Kedvenc szerkesztőnkkel nézzünk bele a <strong>/etc/auto.master</strong> állományba.

A következő sor 
<strong>/media  /etc/auto.media --ghost --timeout=1</strong>
a media alkönyvtár alá fog inditani egy autofs démont, ami további konfigurációval azaz <strong>/etc/auto.media</strong> állományban megadott eszközöket automatikusan fogja kezelni egy-egy alkönyvtárban.

Az <strong>/etc/auto.media</strong> állomany nálam igy néz ki:
<strong>
cdrom           -fstype=iso9660,ro,nodev                       :/dev/scd1
cdwriter        -fstype=iso9660,ro,nodev                       :/dev/scd0
pendrive        -fstype=vfat,rw,uid=1000,gid=1000,umask=002    :/dev/sda1
</strong>

Végül már csak három tennivalónk maradt:
<strong>/etc/default/autofs</strong> állományban kisebb <strong>TIMEOUT=1</strong> értéket állítsunk, készítsük el a gyökér könyvtárát <strong>mkdir /media</strong>
 majd íjraindítani a 
<strong>/etc/init.d/autofs restart</strong>
bekonfigurált szoftvert.

Kellemes hekkelést kívánok!

ui: Az eredeti <a href="http://www.desktop-linux.net/autofs.htm">cikket angolul</a> itt találtam.
