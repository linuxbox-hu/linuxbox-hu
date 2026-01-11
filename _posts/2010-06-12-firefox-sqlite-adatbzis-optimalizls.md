---
excerpt: "Egyszer régen bukkantam a cikkre - sajnos most nem emlékszem a forrásra
  -, ami alapján telepítettem az [http://code.google.com/p/sqlite-manager/ SQLite
  Manager]t. Hogy mire is jó ez?\r\n\r\nNyissuk meg egyenként a Firefox profilban
  (.mozilla/firefox/..../):\r\n* places.sqlite\r\n* urlclassifier3.sqlite\r\n* illetve
  minden nagyobb fájlt...\r\n\r"
categories:
- firefox
layout: story
author: szimszon
title: Firefox SQLite adatbázis optimalizálás
created: 1276341399
---
Egyszer régen bukkantam a cikkre - sajnos most nem emlékszem a forrásra -, ami alapján telepítettem az [http://code.google.com/p/sqlite-manager/ SQLite Manager]t. Hogy mire is jó ez?

Nyissuk meg egyenként a Firefox profilban (.mozilla/firefox/..../):
* places.sqlite
* urlclassifier3.sqlite
* illetve minden nagyobb fájlt...

majd Database -> Compact Database. Ezzel az adatbázis fájlt rendbe tudjuk tenni, és sokszor lényegesen kisebb lesz a mérete...
