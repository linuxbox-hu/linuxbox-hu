---
excerpt: "<p>A <a href=\"http://www.blastfromthepast.se/blabbermouth/2009/10/caffeine-for-linux-1-released/\">Coffeine</a>
  egy kis alkalmazás, mely a gnome-panelen ülve várja, hogy a felhasználó engedélyezze/letitlsa
  a képernyővédőt/suspendet/screen lock-ot.\r\nHasznos lehet flash videók lejátszásánál,
  diavetítés közben ahol a gép,  sokat áll egy képet mutatva, vagy full screen játékok
  játszásakor.\r\nLehet időzíteni is az alkalmazást, hogy meddig tartsa távol az energiatakarékos
  üzemmódot.\r\n\r\n<img src=\"http://linuxbox.hu/sites/linuxbox.hu/files/screenshot_002.png\"></img>\r\n"
categories: []
layout: blog
author: leslie
title: Caffeine - Tarts ébren a géped!
created: 1259266602
---
<p>A <a href="http://www.blastfromthepast.se/blabbermouth/2009/10/caffeine-for-linux-1-released/">Coffeine</a> egy kis alkalmazás, mely a gnome-panelen ülve várja, hogy a felhasználó engedélyezze/letitlsa a képernyővédőt/suspendet/screen lock-ot.
Hasznos lehet flash videók lejátszásánál, diavetítés közben ahol a gép,  sokat áll egy képet mutatva, vagy full screen játékok játszásakor.
Lehet időzíteni is az alkalmazást, hogy meddig tartsa távol az energiatakarékos üzemmódot.

<img src="http://linuxbox.hu/sites/default/files/screenshot_002.png"></img>
<!--break-->
Letöltés útmutató, (ubuntu 9.10-hez)

1. Szerkezd sources.list fájlod:

<b>$gksudo gedit /etc/apt/sources.list</b>

2. Add a következőt a fájlod végéhez:

<b>deb http://ppa.launchpad.net/caffeine-developers/ppa/ubuntu karmic main </b>
Mentsd és zárd be.

3. Vedd fel a PPA kulcsot:

<b>$sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 569113AE</b>

4. Frissítsd a csomaglistád

<b>$sudo apt-get update</b>

5. Instaláld a Caffeine szoftvert :

<b>$sudo apt-get install caffeine</b>

Kész!
 </p>
