---
excerpt: "Legtöbben ismerjük jól az apró <code>cat</code> GNU eszközt amivel szöveges
  állományokat tudunk listázni de azt már nem feltétlen mindenki ismeri, hogy létezik
  az előző eszköz nevének visszafelé kiolvasával elnevezett <code>tac</code> ami fordított
  sorrrendben listázza az állomanyunk, ha erre van szükség. Nekem az imént pont erre
  volt.\r\n"
categories:
- linux
layout: story
author: kecsi
mail: kecsi@linuxbox.hu
title: Szöveges állomány listázása fordított sorrendben; tac
created: 1352471263
---
Legtöbben ismerjük jól az apró <code>cat</code> GNU eszközt amivel szöveges állományokat tudunk listázni de azt már nem feltétlen mindenki ismeri, hogy létezik az előző eszköz nevének visszafelé kiolvasával elnevezett <code>tac</code> ami fordított sorrrendben listázza az állomanyunk, ha erre van szükség. Nekem az imént pont erre volt.
<!--break-->
Egyébként megoldható a probléma vim szövegszerkesztő <code>:g/^/m0</code> parancsával is.

<a href="http://stackoverflow.com/questions/742466/how-can-i-reverse-the-order-of-lines-in-a-file">forrás</a>
