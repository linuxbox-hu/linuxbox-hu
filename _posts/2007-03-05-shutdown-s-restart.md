---
excerpt: "Előfordult már veled, hogy elindítottál egy letöltést és tudtad, hogy mire
  véget ér a letöltés már nem leszel a gép mellet és sokáig nem tudsz visszamenni
  kikapcsolni. Erre a problémára nyújt megoldást a gshutdown nevű program.\r\nLetöltés:
  <a  href=http://download.tuxfamily.org/asher256/dists/edgy/main/binary-i386/gshutdown_0.1-2ubuntu1_i386.deb>gshutdown</a>\r\nEz
  egy egyszerű program, mellyel időzíteni lehet a gép leállítását vagy újraindítását.
  Még nem volt időm kipróbálni, de nagyon kellemes kezelőfelülete van, melyet könnyű
  áttekinteni.\r\n\r"
categories: []
layout: blog
author: sanya
title: Shutdown és restart
created: 1173095359
---
Előfordult már veled, hogy elindítottál egy letöltést és tudtad, hogy mire véget ér a letöltés már nem leszel a gép mellet és sokáig nem tudsz visszamenni kikapcsolni. Erre a problémára nyújt megoldást a gshutdown nevű program.
Letöltés: <a  href=http://download.tuxfamily.org/asher256/dists/edgy/main/binary-i386/gshutdown_0.1-2ubuntu1_i386.deb>gshutdown</a>
Ez egy egyszerű program, mellyel időzíteni lehet a gép leállítását vagy újraindítását. Még nem volt időm kipróbálni, de nagyon kellemes kezelőfelülete van, melyet könnyű áttekinteni.

Azok számára akik otthon vagy kisebb vállalkozásnál szeretnének X-terminált (XDMCP-t) használni a felhasználok kiszolgálására, azoknak a következő kis tippem sokat segíthet.
Alap esetben az X-terminálból való kijelentkezésnél elérhető a hibernálás és alvás gombok, melyekre kattintva a szerver kíméletlenül leáll. Ezeket könnyedén el lehet távolítani! A felhasználó felvétele után be kell jelentkezni a felhasználó nevében és meg kell nyitni a gconf-editor-t. Egyes disztribúciókban ez megtalálható a menüben, de például az Ubuntu-ban csak konzolról indítható. Indítás után az Apps>gnome-power-manager alatt a can_hibernate és a can_suspend pontoknál ki kell venni a pipát. Ezek után már csak a kijelentekzés, képernyő zárolás és a felhasználó váltás érhető el az X-terminálon. Természetesen ezt minden felhasználónál meg kell tenni. Ajánlott még a gconf-editor kiszedése a menüből, hogy a felhasználó véletlen se tudja elindítani.
