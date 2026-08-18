---
author: miamano
categories:
- ubuntu
created: 1161303832
date: '2006-10-20T00:00:00Z'
image:
  path: http://linuxbox.hu/file/IEs4.png
  alt: IEs4Linux
excerpt: 'A napokban telepítettem egy Ubuntut (Drapper). Úgy alakult, hogy elkerülhetetlenné
  vált számomra az Internet Explorer használata.'
title: 'IEs4Linux - Internet Explorert linux alá'
aliases:
- /node/224/
- /story/224/
---
A napokban telepítettem egy Ubuntut (Drapper).
Úgy alakult, hogy elkerülhetetlenné vált számomra az Internet Explorer használata.

Egy okos kis tool a megoldás:
Az [IEs4Linux](http://www.tatanka.com.br/ies4linux/) lényegében egy script halmazt, melynek segítségével egyszerűen használatba vehetjük a sokak által nem különösebben kedvelt, de eléggé elterjedt böngészőt.
A scriptek a nyelvi beállításokat, az IE hozzávalók letöltését és a wine konfigurálását végzik.
<!--break-->
`wget http://www.tatanka.com.br/ies4linux/downloads/ies4linux-2.0.3.tar.gz`
(327K)

Használatához szükségünk lesz [wine](http://packages.ubuntu.com/dapper/otherosfs/wine) (8.5M) és [cabextract](http://packages.ubuntu.com/dapper/utils/cabextract) (44K) csomagok installálására:
Mindekettő szerepel a dapper universe repository-jában.

`apt-get install wine cabextract`

Kicsomagolás után
`tar -xzf ies4linux-2.0.3.tar.gz`
futtassuk a
`ies4linux-2.0.3/ies4linux`
install scriptet.

```
wine: creating configuration directory '/home/miamano/.wine'...
fixme:midi:OSS_MidiInit Synthesizer support MIDI in. Not supported yet (please report)
wine: '/home/miamano/.wine' created successfully.
Wine 0.9.9
Üdvözöljük, miamano! Ez a program az IEs4Linux.
Lehetővé teszi az IE 6, 5.5 és 5.0 Gyors és könnyű telepítését.
Már csak négy kérdést kell megválaszolnia az IE használatáig.
```

A program fel fog tenni néhány kérdést, amire igennel (i) vagy nemmel (n) válaszolhat. Az alapértelmezett minden esetben a félkövéren szedett.

```
Az IE 6 automatikusan települni fog.
Szeretné az IE 5.5 SP2-t is telepíteni? [ i / n ] n
```

```
Szeretné telepíteni az IE 5.01 SP2-t is? [ i / n ] n
```

```
Az IE-k a következő „locale”-k használatával telepíthetőek:
EN-US PT-BR DE FR ES IT NL SV JA KO NO
DA CN TW FI PL HU AR HE CS PT RU EL TR
Alapértelmezett: HU. Gépelje be a választott „locale”-t vagy üssön egy entert az alapértelmezett használatához.
```

```
Alapértelmezésben minden a következő helyre települ: /home/miamano/.ies4linux
A Flash 9 beépülő telepítve lesz, és a program létrehoz munkaasztali indítóikonokat is.
Megfelel ez önnek? (További beállításokért válaszoljon n-t.) [ i / n ]
```

```
A telepítés megkezdése…
A szükséges fájlok letöltése…
```

(Itt jó néhány .exe és .cab kerül letöltésre a Microsoft és a Macromedia oldalairól. 14.5M)

```
[ OK ]
```

```
Telepítés… IE 6
 A telepítés előkészítése
 Wine előtagok létrehozása
 CAB fájlok kibontása
 Inf fájl feldolgozása
 Telepítés… IE 6
 TTF betűkészletek telepítése
 Telepítés… RICHED20
 Telepítés… ActiveX MFC40
 Telepítés… DCOM98
 Registry telepítése
 Telepítés befejezése
[ OK ]
```

```
A Flash Player 9 telepítése…
 Fájlok kicsomagolása
 Flash telepítése ie6
[ OK ]
```

```
Az IEs 4 Linux telepítése befejeződött.
```

```
Az IE-k futtatásához a következő parancsokat használhatja:
 /home/miamano/bin/ie6
```

Konklúzió/Tapasztalatok:

60 Mbyte-nyi hely elegendő volt.
Van még benne pár bug, de produkálta azt az eredményt, amire az IE userek egy weblapnál
panaszkodtak, viszont Firefoxban jól jelent meg.
ISO-8859-2-t jól, de az UTF-8 magyar karaktereket (őű) nálam rosszul kezelte...

Lehetőleg böngészésre ne ezt használjátok! :)
