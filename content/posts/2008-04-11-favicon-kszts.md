---
author: kecsi
categories:
- x
created: 1207924241
date: '2008-04-11T00:00:00Z'
excerpt: 'Ha kis ikont szeretnél készíteni a weboldaladhoz aminek a neve rendszerint favicon.ico akkor azt linux alatt a következő képpen tudod megtenni: * telepítsünk a netpbm nevű csomagot, pl így: apt-get install netpbm * Készítsünk egy 16x16 pixeles kicsi bitmap képet (pl. Gimppel) * Mentsük el a bitmapet .ppm formátumban ("raw mode" kiválasztásával) * Konvertáljuk az elkészített képet a következő paranccsal: ppmtowinicon favicon.ppm > favicon.ico Eredeti okosság angolul.'
title: Favicon készítés
aliases:
- /node/501/
- /story/501/
---
Ha kis ikont szeretnél készíteni a weboldaladhoz aminek a neve rendszerint favicon.ico akkor azt linux alatt a következő képpen tudod megtenni:

    * telepítsünk a netpbm nevű csomagot, pl így: <code>apt-get install netpbm</code>
    * Készítsünk egy 16x16 pixeles kicsi bitmap képet (pl. Gimppel)
    * Mentsük el a bitmapet .ppm formátumban ("raw mode" kiválasztásával)
    * Konvertáljuk az elkészített képet a következő paranccsal: <code>ppmtowinicon favicon.ppm > favicon.ico</code>

<a href="http://workaround.org/moin/FavIcon">Eredeti okosság angolul.</a>
