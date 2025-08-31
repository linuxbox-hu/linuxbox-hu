---
excerpt: "root partició másolása:\r\n<strong>cd /; find -print0 -mount | cpio -p -0
  -d -m -u /masikparticio</strong>\r\nvagy:\r\n<strong>arhiv készítés: find -print0
  -mount|cpio -o -0 -O arhiv.cpio</strong>\r\n<strong>arhivból visszaállítás: cpio
  -i -m -d -u -I arhiv.cpio</strong>"
categories:
- linux
layout: story
author: kecsi
mail: kecsi@linuxbox.hu
title: partició másolás, arhiválás cpio-val
created: 1107213963
---
root partició másolása:
<strong>cd /; find -print0 -mount | cpio -p -0 -d -m -u /masikparticio</strong>
vagy:
<strong>arhiv készítés: find -print0 -mount|cpio -o -0 -O arhiv.cpio</strong>
<strong>arhivból visszaállítás: cpio -i -m -d -u -I arhiv.cpio</strong>
