---
excerpt: "Annak idején írtam az [http://linuxbox.hu/node/645 OWL] dokumentumkezelő
  rendszerről. A használata során sok kényelmetlenség tárult fel. Leginkább az, hogy
  a dokumentumokat külön be kellett scannelni, majd egy weboldalon feltölteni. A készített
  bash segéd script sem bizonyult tuti ötletnek.\r\n\r"
categories: []
layout: blog
author: szimszon
mail: szimszon@oregpreshaz.eu
title: DKR - nagyon kicsi web alapú dokumentum kezelő rendszer síkágyas lapolvasó
  támogatással
created: 1277356269
---
Annak idején írtam az [http://linuxbox.hu/node/645 OWL] dokumentumkezelő rendszerről. A használata során sok kényelmetlenség tárult fel. Leginkább az, hogy a dokumentumokat külön be kellett scannelni, majd egy weboldalon feltölteni. A készített bash segéd script sem bizonyult tuti ötletnek.

Viszont a [http://www.web2py.com web2py] keretrendszerrel amiről korábban [http://linuxbox.hu/node/629 írtam] viszonylag kis erőbefektetéssel lehet egyszerű alkalmazásokat fejleszteni webre.

Így készült el a [https://trac.oregpreshaz.eu/linux/wiki/DKR DKR] is. Ami leginkább szerződések, csekkek, garanciapapírok és hasonlók kezelésére készült.

* A felhasználókezelés csak arra korlátozódik, hogy van-e olyan felhasználó vagy nincs
* A „scanimage” parancs segítségével (sane) olvas be lapokat síkágyas lapolvasóból
* python-imaging segítségével jpg-et készít belőle
* és „convert” program segítségével pdf-et ha több lapból áll a menteni kívánt dokumentum
* nincs dokumentum hierarchia
* címkék vannak
* sablonokat lehet készíteni a különböző dokumentum típusokhoz amikben dátum mezőket lehet definiálni, így pl. automatikusan megadható írja be az öt évvel későbbi dátumot egy helyre.
* angol és magyar nyelv (böngésző nyelve szerint)

Egyenlőre a lapolvasó paraméterezése be van huzalozva a programba, ez lehet később konfigból változtatható lesz.

Google wave: https://wave.google.com/wave/waveref/googlewave.com/w+v0AlALXaA 

Pár képernyőkép:

https://trac.oregpreshaz.eu/linux/raw-attachment/wiki/DKR/index.jpg
https://trac.oregpreshaz.eu/linux/raw-attachment/wiki/DKR/store.jpg
https://trac.oregpreshaz.eu/linux/raw-attachment/wiki/DKR/scanner.jpg
https://trac.oregpreshaz.eu/linux/raw-attachment/wiki/DKR/search.jpg
https://trac.oregpreshaz.eu/linux/raw-attachment/wiki/DKR/template.jpg
