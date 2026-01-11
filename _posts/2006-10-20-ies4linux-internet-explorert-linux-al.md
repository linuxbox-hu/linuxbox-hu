---
excerpt: "<a href=\"http://linuxbox.hu/node/224><img src=\"http://linuxbox.hu/file/IEs4.png\"></a>\r\nA
  napokban telepítettem egy Ubuntut (Drapper).\r\nÚgy alakult, hogy elkerülhetetlenné
  vált számomra az Internet Explorer használata.\r\n\r\nEgy okos kis tool a megoldás:\r\nAz
  <a href=\"http://www.tatanka.com.br/ies4linux/\">IEs4Linux</a> lényegében egy script
  halmazt, melynek segítségével egyszerűen használatba vehetjük a sokak által nem
  különösebben kedvelt, de eléggé elterjedt böngészőt.\r\nA scriptek a nyelvi beállításokat,
  az IE hozzávalók letöltését és a wine konfigurálását végzik.\r\n"
categories:
- ubuntu
layout: story
author: miamano
title: IEs4Linux - Internet Explorert linux alá
created: 1161303832
---
<a href="http://linuxbox.hu/node/224><img src="http://linuxbox.hu/file/IEs4.png"></a>
A napokban telepítettem egy Ubuntut (Drapper).
Úgy alakult, hogy elkerülhetetlenné vált számomra az Internet Explorer használata.

Egy okos kis tool a megoldás:
Az <a href="http://www.tatanka.com.br/ies4linux/">IEs4Linux</a> lényegében egy script halmazt, melynek segítségével egyszerűen használatba vehetjük a sokak által nem különösebben kedvelt, de eléggé elterjedt böngészőt.
A scriptek a nyelvi beállításokat, az IE hozzávalók letöltését és a wine konfigurálását végzik.
<!--break-->
<code>wget http://www.tatanka.com.br/ies4linux/downloads/ies4linux-2.0.3.tar.gz</code>
(327K)

Használatához szükségünk lesz <a href="http://packages.ubuntu.com/dapper/otherosfs/wine">wine</a> (8.5M) és <a href="http://packages.ubuntu.com/dapper/utils/cabextract">cabextract</a> (44K) csomagok installálására:
Mindekettő szerepel a dapper universe repository-jában.

<code>apt-get install wine cabextract</code>

Kicsomagolás után 
<code>tar -xzf ies4linux-2.0.3.tar.gz</code>
futtassuk a
<code>ies4linux-2.0.3/ies4linux</code>
install scriptet.

<code>
wine: creating configuration directory '/home/miamano/.wine'...
fixme:midi:OSS_MidiInit Synthesizer support MIDI in. Not supported yet (please report)
wine: '/home/miamano/.wine' created successfully.
Wine 0.9.9
Üdvözöljük, miamano! Ez a program az IEs4Linux.
Lehetővé teszi az IE 6, 5.5 és 5.0 Gyors és könnyű telepítését.
Már csak négy kérdést kell megválaszolnia az IE használatáig.</code>
<code>
A program fel fog tenni néhány kérdést, amire igennel (i) vagy nemmel (n) válaszolhat. Az alapértelmezett minden esetben a félkövéren szedett.</code>
<code>
Az IE 6 automatikusan települni fog.
Szeretné az IE 5.5 SP2-t is telepíteni? [ i / n ] n</code>
<code>
Szeretné telepíteni az IE 5.01 SP2-t is? [ i / n ] n</code>
<code>
Az IE-k a következő „locale”-k használatával telepíthetőek:
EN-US PT-BR DE FR ES IT NL SV JA KO NO
DA CN TW FI PL HU AR HE CS PT RU EL TR
Alapértelmezett: HU. Gépelje be a választott „locale”-t vagy üssön egy entert az alapértelmezett használatához.</code>
<code>
Alapértelmezésben minden a következő helyre települ: /home/miamano/.ies4linux
A Flash 9 beépülő telepítve lesz, és a program létrehoz munkaasztali indítóikonokat is.
Megfelel ez önnek? (További beállításokért válaszoljon n-t.) [ i / n ]</code>
<code>
A telepítés megkezdése…
A szükséges fájlok letöltése…</code>
##Itt jó néhány .exe és .cab kerül letöltésre a Microsoft és a Macromedia oldalairól.
##(14.5M)
<code>[ OK ]</code>
<code>
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
[ OK ]</code>
<code>
A Flash Player 9 telepítése…
 Fájlok kicsomagolása
 Flash telepítése ie6
[ OK ]</code>
<code>
Az IEs 4 Linux telepítése befejeződött.</code>
<code>
Az IE-k futtatásához a következő parancsokat használhatja:
 /home/miamano/bin/ie6
</code>

Konklúzió/Tapasztalatok:

60 Mbyte-nyi hely elegendő volt.
Van még benne pár bug, de produkálta azt az eredményt, amire az IE userek egy weblapnál
panaszkodtak, viszont Firefoxban jól jelent meg.
ISO-8859-2-t jól, de az UTF-8 magyar karaktereket (őű) nálam rosszul kezelte...

Lehetőleg böngészésre ne ezt használjátok! :)
