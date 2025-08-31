---
excerpt: "Egy VCD replikálása miatt vettem elő ezt az általam már régen is használt
  modult.\r\nLényege, hogy kernelbe illesztés után a cdfs tipussal felcsatolt lemezeket
  ISO-image ként kapjuk meg.\r\n\r\nHogyan tegyünk szert a modulra?\r\n\r\nKapjuk
  le a  csomagot.\r\n~# apt-get install cdfs-src\r\n\r\nmodule-assistant segítségével
  ferdítsük be a modult.\r\n~# module-assistant\r\n\r\nSELECT > válasszuk ki a cdfs
  modult\r"
categories: []
layout: blog
author: grgbox
mail: grgbox@gmail.com
title: CDfs Debian alatt
created: 1236755516
---
Egy VCD replikálása miatt vettem elő ezt az általam már régen is használt modult.
Lényege, hogy kernelbe illesztés után a cdfs tipussal felcsatolt lemezeket ISO-image ként kapjuk meg.

Hogyan tegyünk szert a modulra?

Kapjuk le a  csomagot.
~# apt-get install cdfs-src

module-assistant segítségével ferdítsük be a modult.
~# module-assistant

SELECT > válasszuk ki a cdfs modult
BUILD > ferdítse be a modult
INSTALL> illessze a kernelbe
EXIT

Ez készen is van.

Ellenőrizzük.
~# lsmod |grep cdfs
cdfs                   22344  1

Rendben.
Rendszer indulásakor húzzuk be a modult.
~# echo 'cdfs' >>/etc/modules

Próbáljuk ki.
~# mount -t cdfs /dev/cdrom /mnt/celpont/

~# mount
/dev/scd0 on /mnt/celpont type cdfs (ro)

~# ls /mnt/celpont
sessions_1-1.iso


Jó szórakozást :)

Ezt a leírást csak saját felelősségedre használd. Az esetlegesen bekövetkező károkért semmilyen felelősséget nem vállalok.
A leírás szabadon terjeszthető a szerző feltüntetésével, módosítása csak a szerző beleegyezésével lehetséges.

