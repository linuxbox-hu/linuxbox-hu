---
author: kecsi
categories:
- linux
created: 1352471263
date: '2012-11-09T00:00:00Z'
description: Legtöbben ismerjük jól az apró cat GNU eszközt amivel szöveges állományokat tudunk listázni de azt már nem feltétlen mindenki ismeri, hogy létezik az előző eszköz nevének visszafelé kiolvasával elnevezett tac ami fordított sorrrendben listázza az állomanyunk, ha erre van szükség. Nekem az imént pont erre volt.
title: Szöveges állomány listázása fordított sorrendben; tac
aliases:
- /node/714/
- /story/714/
---
Legtöbben ismerjük jól az apró <code>cat</code> GNU eszközt amivel szöveges állományokat tudunk listázni de azt már nem feltétlen mindenki ismeri, hogy létezik az előző eszköz nevének visszafelé kiolvasával elnevezett <code>tac</code> ami fordított sorrrendben listázza az állomanyunk, ha erre van szükség. Nekem az imént pont erre volt.
<!--break-->
Egyébként megoldható a probléma vim szövegszerkesztő <code>:g/^/m0</code> parancsával is.

<a href="http://stackoverflow.com/questions/742466/how-can-i-reverse-the-order-of-lines-in-a-file">forrás</a>
