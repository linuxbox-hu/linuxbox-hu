---
excerpt: "Escputil egy parancsori alkalmazás Epson nyomtatók kezeléséhez.\r\n\r\nNéhány
  példa mire lehet használni.\r\nPl. tinta szint lekérdezés\r\n<code>escputil -i -u
  -r /dev/usb/lp0</code>\r\ntisztítás:\r\n<code>escputil -c -u -r /dev/usb/lp0</code>\r\nfúvóka
  ellenőrzés:\r\n<code>escputil -n -u -r /dev/usb/lp0</code>\r\nprinter fej beállítás:\r\n<code>escutil
  -a -u -r /dev/usb/lp0</code>\r\nszínes printer fej beállítás:\r\n<code>escputil
  -o -u -r /dev/usb/lp0</code>"
categories:
- linux
layout: story
author: kecsi
title: Epson CLI utasítások
created: 1206005591
---
Escputil egy parancsori alkalmazás Epson nyomtatók kezeléséhez.

Néhány példa mire lehet használni.
Pl. tinta szint lekérdezés
<code>escputil -i -u -r /dev/usb/lp0</code>
tisztítás:
<code>escputil -c -u -r /dev/usb/lp0</code>
fúvóka ellenőrzés:
<code>escputil -n -u -r /dev/usb/lp0</code>
printer fej beállítás:
<code>escutil -a -u -r /dev/usb/lp0</code>
színes printer fej beállítás:
<code>escputil -o -u -r /dev/usb/lp0</code>
