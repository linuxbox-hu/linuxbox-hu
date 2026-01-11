---
excerpt: "Újabb rendszeradminisztrálást segítõ webes alkalmazát szeretnék bemutatni.\r\n[http://linuxbox.hu/node/712
  Elõzõ bejegyzésemben] a dpkg alapú csomagrendszer böngészésére alkalmas oldalt mutattam
  be.\r\n\r\nMost a ''Hálózat'' vizeire eveztem és a '''Tũzfal'''at képszerũen, a
  tũzfalszabályokat szimbólikusan ábrázoló [http://tuxy.dyndns.biz/cgi-bin/iptables/iptables.pl
  weblapot] készítettem.\r\n\r"
categories: []
layout: blog
author: bAndie91
title: vizualizáció II.
created: 1351354573
---
Újabb rendszeradminisztrálást segítõ webes alkalmazát szeretnék bemutatni.
[http://linuxbox.hu/node/712 Elõzõ bejegyzésemben] a dpkg alapú csomagrendszer böngészésére alkalmas oldalt mutattam be.

Most a ''Hálózat'' vizeire eveztem és a '''Tũzfal'''at képszerũen, a tũzfalszabályokat szimbólikusan ábrázoló [http://tuxy.dyndns.biz/cgi-bin/iptables/iptables.pl weblapot] készítettem.

A program az '''iptables''' tũzfalszabályait dolgozza fel és rendel az egyes feltételekhez ikonokat. 
* Feltölthetjük saját tũzfalunkat, alul kell beilleszteni az iptables táblák szabálylistáit. pl.
-P INPUT DROP
-A services -p tcp -m tcp --dport 80 -m comment --comment "http" -j ACCEPT 
* A bejelentkezés funkció arra való, hogy ha van a webszerverhez egyébként login hozzáférésünk (vagy a CGI programban úgy állítjuk be, máshonnan tud minket authentikálni, mondjuk PAM-ból), akkor a rendszer aktuális tũzfalállapotát tölti be és tekinthetjük meg.
Egyelõre egy nem folytonosan üzemelõ gépen van, ha valaki elég merész, felteheti saját kiszolgálójára!

Képek:

http://i.imgur.com/TFdc4.png http://i.imgur.com/EwtSS.png
