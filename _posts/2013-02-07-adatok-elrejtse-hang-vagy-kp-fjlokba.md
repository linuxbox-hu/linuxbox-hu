---
excerpt: "A szteganográfia (steganography) olyan eljárás, amellyel információt rejthetünk
  el meglévő audió- vagy kép fájlunkba úgy, hogy azok tartalma (látszólag) nem változik.
  Természetesen az elrejtett információt megfelelő alkalmazás segítségével visszanyerhetjük.\r\n"
categories:
- linux
layout: story
author: Goosfrabaa
title: Adatok elrejtése hang vagy kép fájlokba
created: 1360249822
---
A szteganográfia (steganography) olyan eljárás, amellyel információt rejthetünk el meglévő audió- vagy kép fájlunkba úgy, hogy azok tartalma (látszólag) nem változik. Természetesen az elrejtett információt megfelelő alkalmazás segítségével visszanyerhetjük.
<!--break-->
Nem árt tudni, hogy ha az állományt újrakódoljuk, akkor a belerejtett adat is elveszik -azaz pl facebookra feltöltött képünk már nem fogja tartalmazni a belekódolt információt (mert a FB újrakódolja a képeket).
A beágyazás tömörítéssel és titkosítással zajlik, amihez plusz jelszó is megadható.

Ha még nincs telepítve, akkor töltsük le és telepítsük a <em>steghide</em> csomagot.
(Multiplatformos alkalmazás révén, akár MS rendszereken is könnyen használhatjuk).
Ez a parancsori alkalmazás <em>jpg, bmp, wav</em> és <em>au</em> formátumú fájlok kezelését teszi lehetővé.

A program által ismert kódoló algoritmusok: <em>cast-128, gost, rijndael-128 </em>(ez az alapértelmezett)<em>, twofish, arcfour, cast-256, loki97, rijndael-192, saferplus, wake, des, rijndael-256, serpent, xtea, blowfish, enigma, rc2</em>.

<ul>
<li><strong>Kódolás</strong>
A következő példa egy titok nevű (korábban létrehozott) fájlt rejt el a kep.jpg fájlban:
<em>steghide embed -cf ./kep.jpg -ef ./titok</em>

Ha az eredeti fájlt nem akarjuk felülírni (és jelszót sem kívánunk megadni), akkor:
<em>steghide embed -cf ./kep.jpg -ef ./titok -p "" -sf ./uj_kep.jpg</em>

Amennyiben a standard bemenetről (nem fájlból) kívánunk adatot megadni:
<em>steghide embed -cf ./kep.jpg -ef - -p "" -sf ./uj_kep.jpg</em>
Figyelem! A fenti példában nincs beágyazott fájl, ezért az adat kicsomagolásakor hibát kapunk, ha nem adunk meg célfájlt.
</li>

<li><strong>Információ egy fájlról</strong>
Egy fájlról megtudhatjuk, hogy tartalmaz -e rejtett tartalmait (és milyet):
<em>steghide info ./kep.jpg</em>
Ha van jelszó, kérni fogja (a -p kapcsolóval meg is lehet adni, vagy ha nincs jelszó akkor a fenti módszerrel kikapcsolható a jelszó kérés).
</li> 
<p>
<br>

<br><li><strong>Dekódolás </strong>
A rejtett adatfájl visszanyerése:
<em>steghide extract -sf ./kep.jpg </em>

Amennyiben nincs beágyazott fájl, meg kell adnunk az új fájlt amibe menti az adatokat:
<em>steghide extract -sf ./kep.jpg -xf ./uj</em>
</li>
</ul>

A steghide man oldala további információkkal szolgál (pl a tömörítés, kódolás területén).
