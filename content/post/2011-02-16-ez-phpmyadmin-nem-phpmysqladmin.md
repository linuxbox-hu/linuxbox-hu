---
author: bAndie91
categories: []
created: 1297887305
date: '2011-02-16T00:00:00Z'
description: |
  A phpmysqladmin segítségével mysql-konzol szerũen adminisztrálhatunk olyan mysql szervereket, melyeket távolról nem tudunk elérni (általában csak localhoston hallgatnak) de egy webszerverrõl igen!
title: Ez PhpMyAdmin? Nem! PhpMySqlAdmin.
aliases:
- /blog/683/
- /node/683/
---
A phpmysqladmin segítségével mysql-konzol szerũen adminisztrálhatunk olyan mysql szervereket, melyeket távolról nem tudunk elérni (általában csak localhoston hallgatnak) de egy webszerverrõl igen!
<!--break-->
Ez a szerver általában egy webhoszting szerver ami mysql adatbázist is nyújt. Fontos még, hogy PHP-t is futtasson, bár ez ma már alapvetõ.

A programnak 2 összetevõje van: 
* a kiszolgáló része egy php szkript, amit a távoli gépre kell tenni úgy, hogy http-sen meg tudjuk hivogatni (mint böngészõbõl). Ez kommunikál a mySql-lel (neki lehet!)
* a kliens pedig egy parancssoros eszköz, ami 
** bash-t,
** awk-t,
** perl-t,
** sed-et
igényel, de ezek is alapvetõ szerszámok egy adatbázisgazda toolbox-jában ;-) Belõle intézhetjük az sql lekéréseket interaktívan, vagy paraméterein keresztül. A kimentet csv-ben vagy ha van lynx/w3m telepítve, akkor szép táblázatba kirajzolva kaphatjuk meg.
(Illetve a titkosított kapcsolatot kliens oldalon is php-val oldottam meg, de ne szólj senkinek...)

http://sourceforge.net/projects/phpmysqladmin/

Teszterek szívesen látottak!
