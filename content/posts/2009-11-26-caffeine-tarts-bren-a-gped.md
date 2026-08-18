---
author: leslie
categories: []
created: 1259266602
date: '2009-11-26T00:00:00Z'
excerpt: |
  <p>A <a href="http://www.blastfromthepast.se/blabbermouth/2009/10/caffeine-for-linux-1-released/">Coffeine</a> egy kis alkalmazás, mely a gnome-panelen ülve várja, hogy a felhasználó engedélyezze/letitlsa a képernyővédőt/suspendet/screen lock-ot.
  Hasznos lehet flash videók lejátszásánál, diavetítés közben ahol a gép,  sokat áll egy képet mutatva, vagy full screen játékok játszásakor.
  Lehet időzíteni is az alkalmazást, hogy meddig tartsa távol az energiatakarékos üzemmódot.
  
  <img src="http://linuxbox.hu/sites/linuxbox.hu/files/screenshot_002.png"></img>
title: 'Caffeine - Tarts ébren a géped!'
aliases:
- /blog/644/
- /node/644/
---
<p>A <a href="http://www.blastfromthepast.se/blabbermouth/2009/10/caffeine-for-linux-1-released/">Coffeine</a> egy kis alkalmazás, mely a gnome-panelen ülve várja, hogy a felhasználó engedélyezze/letitlsa a képernyővédőt/suspendet/screen lock-ot.
Hasznos lehet flash videók lejátszásánál, diavetítés közben ahol a gép,  sokat áll egy képet mutatva, vagy full screen játékok játszásakor.
Lehet időzíteni is az alkalmazást, hogy meddig tartsa távol az energiatakarékos üzemmódot.

<img src="http://linuxbox.hu/sites/default/files/screenshot_002.png"></img>
<!--break-->
Letöltés útmutató, (ubuntu 9.10-hez)

1. Szerkezd sources.list fájlod:

`$gksudo gedit /etc/apt/sources.list`

2. Add a következőt a fájlod végéhez:

`deb http://ppa.launchpad.net/caffeine-developers/ppa/ubuntu karmic main `
Mentsd és zárd be.

3. Vedd fel a PPA kulcsot:

`$sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 569113AE`

4. Frissítsd a csomaglistád

`$sudo apt-get update`

5. Instaláld a Caffeine szoftvert :

`$sudo apt-get install caffeine`

Kész!
 </p>
