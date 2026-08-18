---
author: kecsi
categories:
- linux
created: 1206005591
date: '2008-03-20T00:00:00Z'
excerpt: |-
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
title: Epson CLI utasítások
aliases:
- /node/483/
- /story/483/
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
