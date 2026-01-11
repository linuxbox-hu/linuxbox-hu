---
excerpt: "Aki woodyban jól ismerte az iptables csomagot, talán használta a <strong>/etc/init.d/iptables</strong>
  inicializáló szkriptet. Ezzel a szkripttel lehetett elmenteni különböző firewall
  beállításokat és autómatikusan visszaállítani őket pl. induláskor. Ez a szkript
  <strong>eltűnt</strong> a sargeból.\r\n\r\nAzért vette ki a csomagból a készítője
  ezeket a szkripteket, mert nem lehetett vele mindent jól kezelni.\r\nA csomag README
  állományában megtalálhatjuk, hogy mit ajánl a készítő a szkript kiváltására.\r\n"
categories:
- debian
layout: story
author: kecsi
title: iptables inicializáló szkript sarge-ban
created: 1120677969
---
Aki woodyban jól ismerte az iptables csomagot, talán használta a <strong>/etc/init.d/iptables</strong> inicializáló szkriptet. Ezzel a szkripttel lehetett elmenteni különböző firewall beállításokat és autómatikusan visszaállítani őket pl. induláskor. Ez a szkript <strong>eltűnt</strong> a sargeból.

Azért vette ki a csomagból a készítője ezeket a szkripteket, mert nem lehetett vele mindent jól kezelni.
A csomag README állományában megtalálhatjuk, hogy mit ajánl a készítő a szkript kiváltására.
<!--break-->
Nevezetesen azt, hogy firewall szkriptjeinket a hálózati eszköz inicializálásakor futtassuk az ifupdown segítségével. például ezeknek a soroknak a hozzáadásával a /etc/network/interfaces állományhoz:

auto eth0
iface eth0 inet dhcp
<strong>  pre-up /root/firewall-setup/firewall.setup.sh start
  pre-down /root/firewall-setup/firewall.setup.sh stop
</strong>
