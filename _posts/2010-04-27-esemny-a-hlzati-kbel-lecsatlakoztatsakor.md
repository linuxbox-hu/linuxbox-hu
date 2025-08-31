---
excerpt: "Mert hogy ezt is lehet linux alatt. Azaz ha bedugjuk vagy kihúzzuk a hálózati
  kábelt, szkripteken keresztül vezérelhetjük a bekövetkező esemény(eke)t.\r\n"
categories:
- linux
layout: story
author: Goosfrabaa
mail: gabrea@freemail.hu
title: Esemény a hálózati kábel (le)csatlakoztatásakor
created: 1272404505
---
Mert hogy ezt is lehet linux alatt. Azaz ha bedugjuk vagy kihúzzuk a hálózati kábelt, szkripteken keresztül vezérelhetjük a bekövetkező esemény(eke)t.
<!--break-->
Mindezt az <a href="http://0pointer.de/lennart/projects/ifplugd/">ifplugd</a> program teszi lehetővé számunkra, mely azt hiszem a legtöbb disztribúcióban csomag formájában elérhető.
Az <code>ifplugd.conf</code> fájlban kell megadni a globális beállításokat (pl. hálózati eszközök neve, hangjelzés, futtatandó szkript neve, késleltetés ideje, állapot figyelés gyakorisága stb..), majd el kell indítani az <code>ifplugd</code> démont és máris lehet tesztelni szkriptjeinket.
A leírás szerint WLAN eszközöket is képes kezelni a program.
