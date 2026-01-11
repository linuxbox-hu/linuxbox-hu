---
excerpt: "Nyomtam egy apt-get update/upgrade-et, puff, itt a vége:\r\n<code>\r\nHibák
  történtek a következő feldolgozása során:\r\n firestarter\r\nE: Sub-process /usr/bin/dpkg
  returned an error code (1)\r\n</code>\r\nGondoltam úgy sem kell:\r\n<code>\r\nroot@ubudesk:~#
  apt-get remove firestarter\r\nCsomaglisták olvasása... Kész\r\nFüggőségi fa építése...
  Kész\r\nA következő csomagok el lesznek TÁVOLÍTVA:\r\n  firestarter\r\n0 csomag
  frissítve lesz, 0 új csomag lesz telepítve, 1 el lesz távolítva és 0 nem lesz frissítve.\r\n1
  csomag nincs teljesen telepítve vagy eltávolítva.\r"
categories: []
layout: blog
author: miamano
title: Ubuntu bug?
created: 1178935106
---
Nyomtam egy apt-get update/upgrade-et, puff, itt a vége:
<code>
Hibák történtek a következő feldolgozása során:
 firestarter
E: Sub-process /usr/bin/dpkg returned an error code (1)
</code>
Gondoltam úgy sem kell:
<code>
root@ubudesk:~# apt-get remove firestarter
Csomaglisták olvasása... Kész
Függőségi fa építése... Kész
A következő csomagok el lesznek TÁVOLÍTVA:
  firestarter
0 csomag frissítve lesz, 0 új csomag lesz telepítve, 1 el lesz távolítva és 0 nem lesz frissítve.
1 csomag nincs teljesen telepítve vagy eltávolítva.
0B-t kell letölteni az archívumokból.
Kicsomagolás után 1946kB lemezterület kerül felszabadításra.
Folytatni akarod [Y/n]? Y
(Adatbázis olvasása ... Jelenleg 102116 fájl és könyvtár van telepítve.)
firestarter eltávolítása ...
 * Stopping the Firestarter firewall...                                                                                               [ ok ]
</code>
Meg is örültem, hogy jött +2Mb. :)
Erre:
<code>
root@ubudesk:~# iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination
</code><code>
Chain FORWARD (policy ACCEPT)
target     prot opt source               destination
</code><code>
Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
</code>
Flush meg volt. Indíthatom kézzel a tüzfalindító skriptet...

Mondanom sem kell, a Firefox is frissült. Hogy mitől fagyott meg, arra nem jöttem rá.
<code>
root@ubudesk:~# ps -ef|grep firefox
miamano   6450     1  1 01:37 ?        00:01:10 /usr/lib/firefox/firefox-bin -a firefox
root     20153  5692  0 03:26 pts/0    00:00:00 grep firefox
root@ubudesk:~# kill -9 6450
<code>

Az apró nyavalyák kezelgetése helyett, inkább kipróbálnám a xubuntut.
<a href="http://miamano.eu">http://miamano.eu</a>
