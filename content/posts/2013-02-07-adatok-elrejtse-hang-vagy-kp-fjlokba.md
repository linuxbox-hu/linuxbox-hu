---
author: Goosfrabaa
categories:
- linux
created: 1360249822
date: '2013-02-07T00:00:00Z'
excerpt: 'A szteganográfia (steganography) olyan eljárás, amellyel információt rejthetünk el meglévő audió- vagy kép fájlunkba úgy, hogy azok tartalma (látszólag) nem változik. Természetesen az elrejtett információt megfelelő alkalmazás segítségével visszanyerhetjük.\r\n'
title: Adatok elrejtése hang vagy kép fájlokba
aliases:
- /node/853/
- /story/853/
---
A szteganográfia (steganography) olyan eljárás, amellyel információt rejthetünk el meglévő audió- vagy kép fájlunkba úgy, hogy azok tartalma (látszólag) nem változik. Természetesen az elrejtett információt megfelelő alkalmazás segítségével visszanyerhetjük.
<!--break-->
Nem árt tudni, hogy ha az állományt újrakódoljuk, akkor a belerejtett adat is elveszik -azaz pl facebookra feltöltött képünk már nem fogja tartalmazni a belekódolt információt (mert a FB újrakódolja a képeket).
A beágyazás tömörítéssel és titkosítással zajlik, amihez plusz jelszó is megadható.

Ha még nincs telepítve, akkor töltsük le és telepítsük a `steghide` csomagot.
(Multiplatformos alkalmazás révén, akár MS rendszereken is könnyen használhatjuk).
Ez a parancsori alkalmazás *jpg, bmp, wav* és `au` formátumú fájlok kezelését teszi lehetővé.

A program által ismert kódoló algoritmusok: `cast-128, gost, rijndael-128 `(ez az alapértelmezett)`, twofish, arcfour, cast-256, loki97, rijndael-192, saferplus, wake, des, rijndael-256, serpent, xtea, blowfish, enigma, rc2`.

<ul>
<li>**Kódolás**
A következő példa egy titok nevű (korábban létrehozott) fájlt rejt el a kep.jpg fájlban:
`steghide embed -cf ./kep.jpg -ef ./titok`

Ha az eredeti fájlt nem akarjuk felülírni (és jelszót sem kívánunk megadni), akkor:
`steghide embed -cf ./kep.jpg -ef ./titok -p "" -sf ./uj_kep.jpg`

Amennyiben a standard bemenetről (nem fájlból) kívánunk adatot megadni:
`steghide embed -cf ./kep.jpg -ef - -p "" -sf ./uj_kep.jpg`
Figyelem! A fenti példában nincs beágyazott fájl, ezért az adat kicsomagolásakor hibát kapunk, ha nem adunk meg célfájlt.
</li>

<li>**Információ egy fájlról**
Egy fájlról megtudhatjuk, hogy tartalmaz -e rejtett tartalmait (és milyet):
`steghide info ./kep.jpg`
Ha van jelszó, kérni fogja (a -p kapcsolóval meg is lehet adni, vagy ha nincs jelszó akkor a fenti módszerrel kikapcsolható a jelszó kérés).
</li> 
<p>
<br>

<br><li>**Dekódolás **
A rejtett adatfájl visszanyerése:
`steghide extract -sf ./kep.jpg `

Amennyiben nincs beágyazott fájl, meg kell adnunk az új fájlt amibe menti az adatokat:
`steghide extract -sf ./kep.jpg -xf ./uj`
</li>
</ul>

A steghide man oldala további információkkal szolgál (pl a tömörítés, kódolás területén).
