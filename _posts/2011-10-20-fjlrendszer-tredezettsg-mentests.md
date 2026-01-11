---
excerpt: "Érdekes program a <a href=\"http://www.vleu.net/shake/\">shake</a>. A működő
  rendszer (felcsatolt fájlrendszer) kiválasztott fájljait, könyvtárait képes defragmentálni
  úgy, hogy egyszerűen újraírja a fájlokat.\r\n"
categories:
- linux
layout: story
author: Goosfrabaa
title: Fájlrendszer töredezettség-mentesítés
created: 1319101039
---
Érdekes program a <a href="http://www.vleu.net/shake/">shake</a>. A működő rendszer (felcsatolt fájlrendszer) kiválasztott fájljait, könyvtárait képes defragmentálni úgy, hogy egyszerűen újraírja a fájlokat.
<!--break-->
Használata egyszerű: csatoljuk újra a cél partíciót a <code>user_xattr</code> opcióval (pl <code>mount / -o remount,user_xattr</code>), majd
továbbra is rootként adjuk ki a shake [állomány] parancsot. Az állomány lehet néhány általunk kiválasztott fájl, vagy könytár is. Pl:

<code>shake /usr/share/doc/ vagy shake ./nagyfile</code>

Az aktuális könyvtár .mp3 fájljait töredezettség-mentesíti úgy, hogy a háttértáron már ABC sorrendben helyezkednek el az állományok:
<code>find ./ -iname '*.mp3' | sort | shake</code>

Kapcsolókkal finomhangolható a  program, érdemes a leírását böngészni.
