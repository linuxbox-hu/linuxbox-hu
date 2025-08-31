---
excerpt: "Kezdjük talán az elején. Aki nem ismeri a <a href=\"http://www.realvnc.com/what.html\">vnc
  szoftvert</a> annak leírom, hogy ezzel az eszközzel egy XDCMPhez, terminal szerverhez
  hasonló távoli grafikus hozzáférést tudunk magunknak készíteni az X-es felületünkhöz.
  A szoftver lényege, hogy szinte operációs rendszer függetlenül tudunk létrehozni
  szervert és annak grafikus felületét el tudjuk érni bármely másik operációs rendszerről.\r\n"
categories:
- debian
layout: story
author: kecsi
mail: kecsi@linuxbox.hu
title: vnc szerver kialakítása
created: 1119378842
---
Kezdjük talán az elején. Aki nem ismeri a <a href="http://www.realvnc.com/what.html">vnc szoftvert</a> annak leírom, hogy ezzel az eszközzel egy XDCMPhez, terminal szerverhez hasonló távoli grafikus hozzáférést tudunk magunknak készíteni az X-es felületünkhöz. A szoftver lényege, hogy szinte operációs rendszer függetlenül tudunk létrehozni szervert és annak grafikus felületét el tudjuk érni bármely másik operációs rendszerről.
<!--break-->
Egy szerver telepítése debian rendszeren rendkívül egyszerű: <strong>apt-get install vnc4server</strong>
Azt még tudnunk kell, hogy a kliens csatlakozásakor jelszót kell megadnunk, amit a szerverünk telepítése elótt le kell generálnunk a <strong>vncpasswd</strong> utasítással. Ezután már indíthatjuk is a szerverünk a <strong>vnc4server :1</strong> utasítással.
Linux rendszerről ehhez a szerverhez egy <strong>xvnc4viewer gépnév_vagy_ip:1</strong> utsítással tudunk kapcsolódni. Természetesen fel kell telepítenünk a <strong>xvnc4viewer</strong>  csomagot.
További konfiguráláshoz a ¬/.vnc/xstartup állományban kell megadnunk, hogy milyen ablakkezelőt, egyéb szoftvereket akarunk autómatikusan indítani csatlakozás után.
