---
author: szimszon
categories:
- linux
created: 1149840063
date: '2006-06-09T00:00:00Z'
description: |
  A dolog rém egyszerű csak valamilyen programra van szükség a ''Mozilla''-tól (Thunderbird, Mozilla, Firefox...).
  
  Ha a fent említett programokban vannak használható tanúsítványaink azokat tudjuk felhasználni
title: Digitális aláírás használatának beállítása OpenOffice.org-nál
aliases:
- /node/173/
- /story/173/
---
A dolog rém egyszerű csak valamilyen programra van szükség a Mozilla-tól (Thunderbird, Mozilla, Firefox...).

Ha a fent említett programokban vannak használható tanúsítványaink azokat tudjuk felhasználni

Annyi a dolgunk, hogy az OpenOffice.org indítása előtt (ha automatikusan nem találja meg) beállítjuk a

`MOZILLA_CERTIFICATE_FOLDER`

környezeti változót arra a könyvtárra ahol a mozilla program a mi profilunkat tárolja. Például:

```text
export MOZILLA_CERTIFICATE_FOLDER="/home/szimszon/.mozilla/firefox/29rsfxrn.default/"
```

A tanúsítvány beszerzéséről a Thawte-nél [itt](http://linuxbox.hu/node/531) található egy leírás.

### Dokumentum digitális aláírása

Miután megírtuk a dokumentumot mentsük el.

1. Majd a **Fájl -> Digitális aláírások**ra kattintsunk

   ![](/assets/img/posts/ooo3.png)
2. Kattintsunk a **Hozzáadás...** gombra:

   ![](/assets/img/posts/ooo4.png)
3. Írjuk be a Mozilla-nál használt mester jelszót:

   ![](/assets/img/posts/ooo5.png)
4. Válasszuk ki az aláíráshoz használandó tanúsítványt, majd **OK**:

   ![](/assets/img/posts/ooo6.png)
5. A dokumentumunk ezzel alá is lett írva:

   ![](/assets/img/posts/ooo7.png)

A kis ikonra kattintva információkat kaphatunk az aláírásról.

Fontos, hogy minden mentés az aláírás törlésével jár, így minden mentés után újra be kell állítani az aláírást.
