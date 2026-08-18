---
author: Goosfrabaa
categories:
- firefox
created: 1317197199
date: '2011-09-28T00:00:00Z'
excerpt: |
  Feltetted a legfrissebb Firefoxot, de a bővítményeid (extensions) nem kompatibilisek vele?
title: Firefox frissítés után nem működő bővítmények
aliases:
- /node/701/
- /story/701/
---
Feltetted a legfrissebb Firefoxot, de a bővítményeid (extensions) nem kompatibilisek vele?
<!--break-->
A megoldás (amíg kijön a hivatalos verzió) mindössze annyi, hogy át kell írni a bővítmény(ek) kompatibilitási verzióját:

<ol>
<li>Azonosítsd be a "hibás" bővítmény könyvtárának helyét valahol a `~/.mozilla/firefox/*.default/extensions/ `alatt</li>
<li>Keresd meg benne az `install.rdf` fájlt és nyisd meg egy egyszerű szövegszerkesztővel</li>
<li>Keress <code>Firefox</code> szekciót, amiben szerepel a  <code>maxVersion</code> bejegyzés és írd át nagyobbra. Pl: 
<code>&lt;!-- Firefox --&gt;
.
.
&lt;em:maxVersion&gt;`7.*.*`&lt;/em:maxVersion&gt;<code></li>
<li>Indítsd újra a Firefoxot</li>
</ol>

Ha a bővítmény esetleg `valamilyen.xpi` fájl (tehát nincs külön alkönyvtára), akkor sem veszett az ügy.
Az `xpi` fájlok lényegében `zip`-ek, tehát csak ki kell csomagolni őket valahova, majd a fenti módosítások után újra összecsomagolni (figyelve, hogy .xpi végződést kapjanak) és máris lehet telepíteni őket.

*Természetesen nincs garancia arra, hogy minden bővítmény hiba nélkül használható ez után is (hiszen nem véletlenül nőtt a Firefox verziója), de az esetek nagy részében szerintem nem lesz gond.*
