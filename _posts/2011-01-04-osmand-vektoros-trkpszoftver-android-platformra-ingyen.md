---
excerpt: "OsmAnd, vektoros térképszoftver Android platformra a [http://turistautak.hu]
  -tól átvett ''magyarországi'' és további [http://openmaps.eu] -s térképekkel. \r\n\r\nKöszönet
  '''Trackman'''nak és '''péter68'''nak a hathatós közreműködésért, hogy az [http://openmaps.eu/]
  -nak lehetett OsmAnd kimenete.\r\n"
categories:
- linux
layout: story
author: szimszon
title: OsmAnd, vektoros térképszoftver Android platformra ingyen
created: 1294173630
---
OsmAnd, vektoros térképszoftver Android platformra a [http://turistautak.hu] -tól átvett ''magyarországi'' és további [http://openmaps.eu] -s térképekkel. 

Köszönet '''Trackman'''nak és '''péter68'''nak a hathatós közreműködésért, hogy az [http://openmaps.eu/] -nak lehetett OsmAnd kimenete.
<!--break-->
A program egyenlőre erősen fejlesztés alatt van, a cikk írásakor a 0.5.1beta verziónál tart és nagyon ígéretes.

<h2>Képernyőképet a weboldaláról</h2>

http://wiki.openstreetmap.org/w/images/e/e2/Android-osmand-filter_poi.png http://wiki.openstreetmap.org/w/images/b/bc/Android-osmand-address.png
http://wiki.openstreetmap.org/w/images/a/aa/Android-osmand-pedestrian.png http://wiki.openstreetmap.org/w/images/9/96/Android-osmand-routing.png

<h2>Adatok</h2>

'''Hivatalos weboldal:''' http://osmand.net/
'''Friss verzió a szoftverből:''' http://code.google.com/p/osmand/downloads/list pl.: [http://code.google.com/p/osmand/downloads/detail?name=OsmAnd-0.5.1beta-b3.apk&can=2&q= OsmAnd-0.5.1beta-b3.apk]
'''Legfrissebb teszt verzió:''' http://download.osmand.net/night-builds/

<h3>Ahol követheted a fejlődést</h3>

'''Google code oldal:''' http://code.google.com/p/osmand/
'''Google group:''' http://groups.google.com/group/osmand

<h2>Érdemes róla tudni</h2>
.
* offline módon is képes dolgozni
* elérhetők rá az http://openmaps.eu térképei
* vektoros adatokkal dolgozik, pár 10 MB-os fájlba elfér egész Magyarország
* alapvetően az OpenStreetMap térképére támaszkodik, abból az adatbázisból keletkező térképadatokat a programmal közvetlenül le lehet tölteni, így nem kell számítógép a térképek előállításához
* magyarra fordítása folyamatban van, ha hibát láttok benne írjátok meg a szimszon @ oregpreshaz.eu címre :)
* útvonaltervezést egyenlőre csak Internet felhasználásával lehetséges, jelenleg fejlesztik az kapcsolat nélküli megoldást

<h2>Telepítés és az openmaps.eu-s térképek</h2>

Telepítéshez én az Astro fájlkezelőt használom Androidon (http://www.metago.net/astro/fm/download.php), a letöltött ''.apk'' -t fel kell másolni az sd kártyára, és az Astro fájlkezelővel lehet telepíteni. Telepítés során létrejön a kártyán egy ''osmand/'' könyvtár, benne több könyvtárral.
A program első indításakor egyből fel is ajánlja az index (térkép) adatok letöltését, ehhez azért érdemes WiFi kapcsolattal rendelkezni. Ha az Internetről ilyen módon letöltöttük az adatokat, már használhatjuk is.

Amennyiben [http://openmaps.eu] -s térképeket szeretnénk használni ahhoz el kell látogatni a [http://openmaps.eu/letoltes] oldalra ahol ki kell választani azt az országot pl. http://openmaps.eu/downloads/hungary itt meg kell keresni a '''OsmAnd térképek''' részt ahonnan már le lehet tölteni a '''_osmand.zip''' fájlt. Ezt a fájlt kell kicsomagolni és a benne lévő két fájlt be kell másolni az sd kártya osmand/ könyvtára alá, úgy hogy a '''.obf''' kiterjesztésű fájl az sd kártya '''osmand/''' könyvtárába kerüljön a '''POI/...odb''' fájl az sd kártya '''osmand/POI''' könyvtárába.

Ha ez megvan a program indulása után érdemes bemenni a '''Beállítások -> Adatok kapcsolat nélküli munkához -> Index adatok újraolvasása''' menüpontra. Így biztos hogy a frissen feltelepített térképekről is tudomást szerez a program.

Mindenkinek kellemes turázást!

'''Frissítés: 2011.01.29'''

Az [http://openmaps.eu] -nak köszönhetően az OsmAnd programból közvetlenül letölthetők az [http://openmaps.eu] -s térképek. Köszönet minden közreműködőnek!
