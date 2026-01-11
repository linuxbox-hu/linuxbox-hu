---
excerpt: "Feltetted a legfrissebb Firefoxot, de a bővítményeid (extensions) nem kompatibilisek
  vele?\r\n"
categories:
- firefox
layout: story
author: Goosfrabaa
title: Firefox frissítés után nem működő bővítmények
created: 1317197199
---
Feltetted a legfrissebb Firefoxot, de a bővítményeid (extensions) nem kompatibilisek vele?
<!--break-->
A megoldás (amíg kijön a hivatalos verzió) mindössze annyi, hogy át kell írni a bővítmény(ek) kompatibilitási verzióját:

<ol>
<li>Azonosítsd be a "hibás" bővítmény könyvtárának helyét valahol a <strong>~/.mozilla/firefox/*.default/extensions/ </strong>alatt</li>
<li>Keresd meg benne az <strong>install.rdf</strong> fájlt és nyisd meg egy egyszerű szövegszerkesztővel</li>
<li>Keress <code>Firefox</code> szekciót, amiben szerepel a  <code>maxVersion</code> bejegyzés és írd át nagyobbra. Pl: 
<code>&lt;!-- Firefox --&gt;
.
.
&lt;em:maxVersion&gt;<strong>7.*.*</strong>&lt;/em:maxVersion&gt;<code></li>
<li>Indítsd újra a Firefoxot</li>
</ol>

Ha a bővítmény esetleg <strong>valamilyen.xpi</strong> fájl (tehát nincs külön alkönyvtára), akkor sem veszett az ügy.
Az <strong>xpi</strong> fájlok lényegében <strong>zip</strong>-ek, tehát csak ki kell csomagolni őket valahova, majd a fenti módosítások után újra összecsomagolni (figyelve, hogy .xpi végződést kapjanak) és máris lehet telepíteni őket.

<em>Természetesen nincs garancia arra, hogy minden bővítmény hiba nélkül használható ez után is (hiszen nem véletlenül nőtt a Firefox verziója), de az esetek nagy részében szerintem nem lesz gond.</em>
