---
author: attisan
categories:
- ubuntu
created: 1159686304
date: '2006-10-01T00:00:00Z'
description: 'Kedvenc ubuntunk alatt is találkozhatunk azzal a bosszantó jelenséggel, hogy a wmv (és más windowsos formátumokat) fájlokat nem tudjuk lejátszani. Illetve ha igen, akkor csak hangjuk van, a kép meg sehol. A probléma megoldásához csak az mplayer-t és a w32codecs csomagot kell telepítenünk. Az mplayer elérhető a multiverse repo-k engedélyezésével. Egy frissített codec packot pedig itt találsz: Az /etc/apt/sources list végére írd: deb http://cle.linux.org.tw/candyz/Ubuntu i386/ Kulcs import: wget http://cle.linux.org.tw/candyz/Ubuntu/candyz.key -O -|sudo apt-key add -'
title: Wmv fájlok lejátszásához szükséges codec-ek
aliases:
- /node/214/
- /story/214/
---
Kedvenc ubuntunk alatt is találkozhatunk azzal a bosszantó jelenséggel, hogy a wmv (és más windowsos formátumokat) fájlokat nem tudjuk lejátszani. Illetve ha igen, akkor csak hangjuk van,  a kép meg sehol.

A probléma megoldásához csak az mplayer-t és a w32codecs csomagot kell telepítenünk. Az mplayer elérhető a multiverse repo-k engedélyezésével. Egy frissített codec packot pedig itt találsz:

Az /etc/apt/sources list végére írd:
deb http://cle.linux.org.tw/candyz/Ubuntu i386/

Kulcs import:
wget http://cle.linux.org.tw/candyz/Ubuntu/candyz.key -O -|sudo apt-key add -

Aztán frissítés: apt-get update és telepítés: apt-get install w32codecs
