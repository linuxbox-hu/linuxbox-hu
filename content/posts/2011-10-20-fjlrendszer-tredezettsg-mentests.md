---
author: Goosfrabaa
categories:
- linux
created: 1319101039
date: '2011-10-20T00:00:00Z'
excerpt: |
  Érdekes program a <a href="http://www.vleu.net/shake/">shake</a>. A működő rendszer (felcsatolt fájlrendszer) kiválasztott fájljait, könyvtárait képes defragmentálni úgy, hogy egyszerűen újraírja a fájlokat.
title: Fájlrendszer töredezettség-mentesítés
aliases:
- /node/705/
- /story/705/
---
Érdekes program a <a href="http://www.vleu.net/shake/">shake</a>. A működő rendszer (felcsatolt fájlrendszer) kiválasztott fájljait, könyvtárait képes defragmentálni úgy, hogy egyszerűen újraírja a fájlokat.
<!--break-->
Használata egyszerű: csatoljuk újra a cél partíciót a <code>user_xattr</code> opcióval (pl <code>mount / -o remount,user_xattr</code>), majd
továbbra is rootként adjuk ki a shake [állomány] parancsot. Az állomány lehet néhány általunk kiválasztott fájl, vagy könytár is. Pl:

<code>shake /usr/share/doc/ vagy shake ./nagyfile</code>

Az aktuális könyvtár .mp3 fájljait töredezettség-mentesíti úgy, hogy a háttértáron már ABC sorrendben helyezkednek el az állományok:
<code>find ./ -iname '*.mp3' | sort | shake</code>

Kapcsolókkal finomhangolható a  program, érdemes a leírását böngészni.
