---
excerpt: "A dolog rém egyszerű csak valamilyen programra van szükség a ''Mozilla''-tól
  (Thunderbird, Mozilla, Firefox...).\r\n\r\nHa a fent említett programokban vannak
  használható tanúsítványaink azokat tudjuk felhasználni\r\n"
categories:
- linux
layout: story
author: szimszon
title: Digitális aláírás használatának beállítása OpenOffice.org-nál
created: 1149840063
---
A dolog rém egyszerű csak valamilyen programra van szükség a ''Mozilla''-tól (Thunderbird, Mozilla, Firefox...).

Ha a fent említett programokban vannak használható tanúsítványaink azokat tudjuk felhasználni
<!--break-->
Annyi a dolgunk, hogy az OpenOffice.org indítása előtt (ha automatikusan nem találja meg) beállítjuk a

'''MOZILLA_CERTIFICATE_FOLDER'''

környezeti változót arra a könyvtárra ahol a mozilla program a mi profilunkat tárolja. Például:

'''export MOZILLA_CERTIFICATE_FOLDER="
/home/szimszon/.mozilla/firefox/29rsfxrn.default/" '''

A tanúsítvány beszerzéséről a Thawte-nél [http://linuxbox.hu/node/531 itt] található egy leírás.

=== Dokumentum digitális aláírása ===

Miután megírtuk a dokumentumot mentsük el.

# Majd a '''Fájl -> Digitális aláírások'''ra kattintsunk<br>http://linuxbox.hu/sites/default/files/ooo3.png
# Kattintsunk a '''Hozzáadás...''' gombra: <br>http://linuxbox.hu/sites/default/files/ooo4.png
# Írjuk be a Mozilla-nál használt mester jelszót: <br>http://linuxbox.hu/sites/default/files/ooo5.png
# Válasszuk ki az aláíráshoz használandó tanúsítványt, majd '''OK''': <br>http://linuxbox.hu/sites/default/files/ooo6.png
# A dokumentumunk ezzel alá is lett írva: <br>http://linuxbox.hu/sites/default/files/ooo7.png

A kis ikonra kattintva információkat kaphatunk az aláírásról.

Fontos, hogy minden mentés az aláírás törlésével jár, így minden mentés után újra be kell állítani az aláírást.
