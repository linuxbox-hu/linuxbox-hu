---
author: kecsi
categories:
- linux
created: 1107213842
date: '2005-01-31T00:00:00Z'
excerpt: 'Particiót 8e tipusúra, majd pvcreate, vgcreate, lvcreate, mke2fs és mountolás
  lépésekben az LVM kialakításához.'
title: Linux Volume Manager (LVM)
aliases:
- /node/6/
- /story/6/
---
1. Készítsünk el egy particiót vagy többet, amiknek `8e` tipusunak kell lennie!
2. `pvcreate /dev/hda3` --- előkészítjük a hozzáadandó partícókat, mind!
3. `vgcreate -s 16M test /dev/hdb2 /dev/hda3` -- hozzádjuk a particiókat egy csoporthoz
4. `lvcreate oralv oravg`
&nbsp;-- Létrehozzuk a lvm-et. Itt lehet pl a stripeot is definialni a -i kapcsoloval
&nbsp;pl.: `lvcreate -n trylv -i 2 -I 8 -L 85G tryvg`
5. Majd készitsünk filerendszert az lvm-ünk fölé: `mke2fs /dev/oravg/oralv`
6. mountoljuk fel azt, fstab..
