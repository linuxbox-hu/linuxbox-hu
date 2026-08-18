---
author: kecsi
categories:
- debian
created: 1119378842
date: '2005-06-21T00:00:00Z'
excerpt: Kezdjük talán az elején. Aki nem ismeri a vnc szoftvert annak leírom, hogy ezzel az eszközzel egy XDCMPhez, terminal szerverhez hasonló távoli grafikus hozzáférést tudunk magunknak készíteni az X-es felületünkhöz. A szoftver lényege, hogy szinte operációs rendszer függetlenül tudunk létrehozni szervert és annak grafikus felületét el tudjuk érni bármely másik operációs rendszerről.
title: vnc szerver kialakítása
aliases:
- /node/79/
- /story/79/
---
Kezdjük talán az elején. Aki nem ismeri a <a href="http://www.realvnc.com/what.html">vnc szoftvert</a> annak leírom, hogy ezzel az eszközzel egy XDCMPhez, terminal szerverhez hasonló távoli grafikus hozzáférést tudunk magunknak készíteni az X-es felületünkhöz. A szoftver lényege, hogy szinte operációs rendszer függetlenül tudunk létrehozni szervert és annak grafikus felületét el tudjuk érni bármely másik operációs rendszerről.
<!--break-->
Egy szerver telepítése debian rendszeren rendkívül egyszerű: `apt-get install vnc4server`
Azt még tudnunk kell, hogy a kliens csatlakozásakor jelszót kell megadnunk, amit a szerverünk telepítése elótt le kell generálnunk a `vncpasswd` utasítással. Ezután már indíthatjuk is a szerverünk a `vnc4server :1` utasítással.
Linux rendszerről ehhez a szerverhez egy `xvnc4viewer gépnév_vagy_ip:1` utsítással tudunk kapcsolódni. Természetesen fel kell telepítenünk a `xvnc4viewer`  csomagot.
További konfiguráláshoz a ¬/.vnc/xstartup állományban kell megadnunk, hogy milyen ablakkezelőt, egyéb szoftvereket akarunk autómatikusan indítani csatlakozás után.
