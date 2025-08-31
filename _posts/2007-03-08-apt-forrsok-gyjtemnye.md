---
excerpt: "Találtam egy APT forrásokat gyűjtő oldalt, melyről letölthető az Edgy-hez
  egy deb csomag, amely beteszi a készítő által talált forrásokat a sources.list fájlba.\r\nLetöltés:
  <a href=http://3v1n0.tuxfamily.org/pool/edgy/3v1n0/3v1n0-sources-list_0.3-3v1ubuntu0edgy1_i386.deb>APT
  gyűjtemény</a>\r\n\r\nMindenkit figyelmeztetek, hogy csak saját felelőségére telepítse
  a csomagot!\r\n\r\nTelepítési tapasztalatok:\r"
categories: []
layout: blog
author: sanya
mail: snagy.sandor@gmail.com
title: APT források gyűjteménye
created: 1173346832
---
Találtam egy APT forrásokat gyűjtő oldalt, melyről letölthető az Edgy-hez egy deb csomag, amely beteszi a készítő által talált forrásokat a sources.list fájlba.
Letöltés: <a href=http://3v1n0.tuxfamily.org/pool/edgy/3v1n0/3v1n0-sources-list_0.3-3v1ubuntu0edgy1_i386.deb>APT gyűjtemény</a>

Mindenkit figyelmeztetek, hogy csak saját felelőségére telepítse a csomagot!

Telepítési tapasztalatok:
Elsőre mindenki azt fogja gondolni, hogy könnyedén telepíthető. Részben igaz, mivel a csomag szó nélkül települ, viszont kulcsokat nem telepít! Azokat a forrásokat, melyeket csak a hitelesítő kulccsal lehet használni egyesével fel kell keresnünk és le kell tölteni a szükséges kulcsot vagy a sourdes.list fájlból ki kell másolni a kulcs útvonalát és wget-tel kell letölteni. Kulcstelepítést végezhetünk apt-key add utasítással vagy a synaptic tárolók ablakában grafikusan.

Letölthető csomagokkal kapcsolatos tapasztalatok:
Találtam néhány hasznos csomagot, melyekről később bővebben írok, de sajnos a legtöbb esetben negatív tapasztalatokat szereztem a csomagokkal kapcsolatban. Az első zavaró jelenség ami jelentkezik, hogy rengeteg csomagra a szoftverfrissítő szolgáltatás azt állítja frissebb, mint a telepített változat. Ennek oka, hogy a csomag verziószáma hiába egyezik meg, ha mögötte egy medibuntu felírat miatt (illetve valószínűleg az elkészítés dátuma miatt) frissebbnek hiszi a telepítőnk. Másik zavaró gond, hogy az újonnan beszerzett csomag hibás lehet, mely adódhat abból, hogy olyan gépen lett lefordítva, mely nagyon eltér a saját gépünk konfigurációjától. Sajnos az ATI telepítőt frissítettem és azóta a 3D-es alkalmazások egy része nem működik. Mivel nem vagyok guru, így marad megoldásnak a régi ATI csomag visszatelepítése, reménykedve abba, hogy helyreáll a rendszer.
