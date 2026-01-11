---
excerpt: "1. Készítsünk el egy particiót vagy többet, amiknek <strong>8e</strong>
  tipusunak kell lennie!\r\n2. <strong>pvcreate /dev/hda3</strong> --- előkészítjük
  a hozzáadandó partícókat, mind!\r\n3. <strong>vgcreate -s 16M test /dev/hdb2 /dev/hda3</strong>
  -- hozzádjuk a particiókat egy csoporthoz\r\n4. <strong>lvcreate oralv oravg</strong>
  \r\n&nbsp;-- Létrehozzuk a lvm-et. Itt lehet pl a stripeot is definialni a -i kapcsoloval
  \r\n&nbsp;pl.: <strong>lvcreate -n trylv -i 2 -I 8 -L 85G tryvg</strong>\r\n5. Majd
  készitsünk filerendszert az lvm-ünk fölé: <strong>mke2fs /dev/oravg/oralv</strong>\r"
categories:
- linux
layout: story
author: kecsi
title: Linux Volume Manager (LVM)
created: 1107213842
---
1. Készítsünk el egy particiót vagy többet, amiknek <strong>8e</strong> tipusunak kell lennie!
2. <strong>pvcreate /dev/hda3</strong> --- előkészítjük a hozzáadandó partícókat, mind!
3. <strong>vgcreate -s 16M test /dev/hdb2 /dev/hda3</strong> -- hozzádjuk a particiókat egy csoporthoz
4. <strong>lvcreate oralv oravg</strong> 
&nbsp;-- Létrehozzuk a lvm-et. Itt lehet pl a stripeot is definialni a -i kapcsoloval 
&nbsp;pl.: <strong>lvcreate -n trylv -i 2 -I 8 -L 85G tryvg</strong>
5. Majd készitsünk filerendszert az lvm-ünk fölé: <strong>mke2fs /dev/oravg/oralv</strong>
6. mountoljuk fel azt, fstab..
