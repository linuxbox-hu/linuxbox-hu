---
layout: post
title: KeePass2 a jelszótároló mindenes
date: 2013-04-08
author: szimszon
categories: [linux]
tags:
 - keepass
 - KeePass2
 - keefox
excerpt: Kell egy olyan program ami intelligensen kezeli a millió egy jelszót?
---
## KeePass Password Safe  

[KeePass Password Safe](https://keepass.info/)

Kell egy olyan program ami intelligensen kezeli a millió egy jelszót? A jelszavakat titkosítva tárolja és átjárható az operációs rendszerek között beleértve az Androidot is?

 Tegnap este akadtam rá a KeePass 2.x-es változatára ami megfelelőnek tűnik.

 * AES, Rijndael (SHA-256 hash) titkosítás használata a jelszavak tárolására
 * Az adatbázis jelszóval és/vagy kulcsfájllal is védhető
 * Létezik Win98 / WinME / Win2000 / Win XP... verzió (.Net keretrendszer kell hozzá), Linux, BSD (Mono keretrendszer kell hozzá), Mac OS X, PocketPC, Smartphone. Letöltés [Letölés oldal](https://keepass.info/download.html).
 * Exportálás TXT, HTML, XML, CSV struktúrába
 * Importálás Password Keeper-ből, Password Agent-ből, CodeWalletPro, Password Safe v2 [Help: Import](https://keepass.info/help/base/importexport.html)
 * Az egész adatbázis egy fájl
 * Fájl csatolmányok adhatók a bejegyzésekhez
 * Auto-type, az ablak címe alapján kikeresi a megfelelő bejegyzést és automatikusan beírja (képes arra, hogy az egyik felét a jelszónak billentyűzet emulációval a másik felét vágólapról betenni - így nehezítve a dolgát a keyloggereknek vagy vágólap figyelőknek)
 * Csoportok, al-csoportok kezelése
 * Több adatbázis együttes használata
 * Kiterjesztésekkel bővíthető funkcionalitás (Figyelem van ami csak Windows only :( )
 * Nyílt forráskód. KeePass is OSI Certified Open Source Software. OSI Certified is a certification mark of the Open Source Initiative.

[Letölés oldal](https://keepass.info/download.html).

Még egy érdekes bővitményre hívnám fel a figyelmet a [rengeteg másik plugin](https://keepass.info/plugins.html) Figyelem, vannak Windows ONLY kiterjesztések. Ez az [KeeFox](https://keefox.org/), melynek használatával a Firefox beépített jelszókezelőjét tudjuk kiváltani úgy, hogy a jelszavak nem a böngészőbe kerül elmentésre, hanem a KeePass v2 adatbázisába, amit egy RPC hívással képes elérni. Linux alatt Ubuntut használva a KeePass plugin könyvtára: /usr/lib/keepass2/plugins. Azon kívül ajánlatos telepíteni a teljes Mono keretrendszert (mono-complete), különben a KeeFox bővitmény nem fog működni.

Aki nem akar a KeeFox-szal bajlódni annak még mindig ott van az Auto-type, amihez Linux alatt az [xdotool](https://github.com/jordansissel/xdotool) csomag szüksége ami X alatt képes billentyűzetet és egeret emulálni. Unity alatt _Rendszerbeállítások -> Billentyűzet -> Gyorsbillentyűk -> Egyedi..._ Név: **KeePass Auto-Type**, Parancs: **/usr/bin/keepass2 --auto-type** majd adjunk hozzá egy kívánt billentyű kombinációt, pl.: `<CTRL>+<ALT>+A`

Kellemes ismerkedést a programmal.
