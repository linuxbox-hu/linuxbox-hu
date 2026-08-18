---
author: leslie
categories: []
created: 1222852792
date: '2008-10-01T00:00:00Z'
description: Hosszas béta fázist követően elindult az online háttértárat kínáló Dropbox. A multiplatform szolgáltatás alapcsomagja bárki által ingyenesen igénybe vehető. Alapból 2GB tárhelyet kapunk, de némi pénzért további kapacitáshoz is juthatunk.
title: 'Online háttértár - DropBox'
aliases:
- /blog/554/
- /node/554/
---
Hosszas béta fázist követően elindult az online háttértárat kínáló Dropbox. A multiplatform szolgáltatás alapcsomagja bárki által ingyenesen igénybe vehető. Alapból 2GB tárhelyet kapunk, de némi pénzért további kapacitáshoz is juthatunk.

![](/assets/img/posts/ScFileBrowser.png)

Ha letöltöttük a kliens programot, és újraindítottuk a grafikus rendszerünket, akkor megjelenik egy regisztrációs ablak. Név, email cím és, jelszó megadása után miénk is a 2GB. A nautilus-ba és a gnome-panelba is szépen beépül a program.

Létrehoz a home könyvtárunkban egy Dropbox nevű mappát (igény szerint máshogy is lehet nevezni), és annak tartalmát szinkronizálja egy szerverrel. Hogy a mappában található adatok milyen státuszban (firssített, frissítés alatt, nem frissített) vannak a szerveren található adatokhoz képest, azt egy kis pictogramm jelzi a mappa felett.

![](/assets/img/posts/ScPanes.png)

A gnome panelban megjelenő kisikonra kattintva, láthatjuk, hogy tárhelyünknek mekkora részét használjuk ki, illetve itt van lehetőségünk további beállításokat módosítani (max fel- és letöltési sebesség, proxy, stb...)

Letölthető [innen](http://www.getdropbox.com/), de van ubuntu tároló is:

```text
deb http://www.getdropbox.com/static/ubuntu hardy main
deb-src http://www.getdropbox.com/static/ubuntu hardy main
```

