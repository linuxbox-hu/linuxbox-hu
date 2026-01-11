---
excerpt: "Ha kis ikont szeretnél készíteni a weboldaladhoz aminek a neve rendszerint
  favicon.ico akkor azt linux alatt a következő képpen tudod megtenni:\r\n\r\n    *
  telepítsünk a netpbm nevű csomagot, pl így: <code>apt-get install netpbm</code>\r\n
  \   * Készítsünk egy 16x16 pixeles kicsi bitmap képet (pl. Gimppel)\r\n    * Mentsük
  el a bitmapet .ppm formátumban (\"raw mode\" kiválasztásával)\r\n    * Konvertáljuk
  az elkészített képet a következő paranccsal: <code>ppmtowinicon favicon.ppm > favicon.ico</code>\r\n\r\n<a
  href=\"http://workaround.org/moin/FavIcon\">Eredeti okosság angolul.</a>"
categories:
- x
layout: story
author: kecsi
title: Favicon készítés
created: 1207924241
---
Ha kis ikont szeretnél készíteni a weboldaladhoz aminek a neve rendszerint favicon.ico akkor azt linux alatt a következő képpen tudod megtenni:

    * telepítsünk a netpbm nevű csomagot, pl így: <code>apt-get install netpbm</code>
    * Készítsünk egy 16x16 pixeles kicsi bitmap képet (pl. Gimppel)
    * Mentsük el a bitmapet .ppm formátumban ("raw mode" kiválasztásával)
    * Konvertáljuk az elkészített képet a következő paranccsal: <code>ppmtowinicon favicon.ppm > favicon.ico</code>

<a href="http://workaround.org/moin/FavIcon">Eredeti okosság angolul.</a>
