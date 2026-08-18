---
author: kecsi
categories:
- debian
created: 1120677969
date: '2005-07-06T00:00:00Z'
excerpt: |
  Aki woodyban jól ismerte az iptables csomagot, talán használta a <strong>/etc/init.d/iptables</strong> inicializáló szkriptet. Ezzel a szkripttel lehetett elmenteni különböző firewall beállításokat és autómatikusan visszaállítani őket pl. induláskor. Ez a szkript <strong>eltűnt</strong> a sargeból.
  
  Azért vette ki a csomagból a készítője ezeket a szkripteket, mert nem lehetett vele mindent jól kezelni.
  A csomag README állományában megtalálhatjuk, hogy mit ajánl a készítő a szkript kiváltására.
title: iptables inicializáló szkript sarge-ban
aliases:
- /node/84/
- /story/84/
---
Aki woodyban jól ismerte az iptables csomagot, talán használta a `/etc/init.d/iptables` inicializáló szkriptet. Ezzel a szkripttel lehetett elmenteni különböző firewall beállításokat és autómatikusan visszaállítani őket pl. induláskor. Ez a szkript **eltűnt** a sargeból.

Azért vette ki a csomagból a készítője ezeket a szkripteket, mert nem lehetett vele mindent jól kezelni.
A csomag README állományában megtalálhatjuk, hogy mit ajánl a készítő a szkript kiváltására.
<!--break-->
Nevezetesen azt, hogy firewall szkriptjeinket a hálózati eszköz inicializálásakor futtassuk az ifupdown segítségével. például ezeknek a soroknak a hozzáadásával a /etc/network/interfaces állományhoz:

auto eth0
iface eth0 inet dhcp
```text
  pre-up /root/firewall-setup/firewall.setup.sh start
  pre-down /root/firewall-setup/firewall.setup.sh stop
```
