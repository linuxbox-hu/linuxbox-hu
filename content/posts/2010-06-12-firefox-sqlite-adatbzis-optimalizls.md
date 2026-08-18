---
author: szimszon
categories:
- firefox
created: 1276341399
date: '2010-06-12T00:00:00Z'
excerpt: 'Egyszer régen bukkantam a cikkre - sajnos most nem emlékszem a forrásra -, ami alapján telepítettem az [http://code.google.com/p/sqlite-manager/ SQLite Manager]t. Hogy mire is jó ez? Nyissuk meg egyenként a Firefox profilban (.mozilla/firefox/..../): * places.sqlite * urlclassifier3.sqlite * illetve minden nagyobb fájlt...'
title: Firefox SQLite adatbázis optimalizálás
aliases:
- /node/666/
- /story/666/
---
Egyszer régen bukkantam a cikkre - sajnos most nem emlékszem a forrásra -, ami alapján telepítettem az [http://code.google.com/p/sqlite-manager/ SQLite Manager]t. Hogy mire is jó ez?

Nyissuk meg egyenként a Firefox profilban (.mozilla/firefox/..../):
* places.sqlite
* urlclassifier3.sqlite
* illetve minden nagyobb fájlt...

majd Database -> Compact Database. Ezzel az adatbázis fájlt rendbe tudjuk tenni, és sokszor lényegesen kisebb lesz a mérete...
