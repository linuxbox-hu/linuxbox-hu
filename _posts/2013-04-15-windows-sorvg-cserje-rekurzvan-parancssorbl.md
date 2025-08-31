---
excerpt: "Hosszú évek után a múlt héten találkoztam újra azzal a problémával, hogy
  egy macintos rendszerben fejlesztett kódot, amihez egy windows-os környezetben is
  hozzányúltak, kellett bevezetnem verziókezelőbe. 2013 ide vagy oda, a sorvégek még
  mindíg gondot tudnak okozni a közös munka folyamán.\r"
categories:
- linux
layout: story
author: vandor
mail: vandor@mezitlab.eu
title: Windows sorvég cseréje rekurzívan, parancssorból
created: 1366035062
---
Hosszú évek után a múlt héten találkoztam újra azzal a problémával, hogy egy macintos rendszerben fejlesztett kódot, amihez egy windows-os környezetben is hozzányúltak, kellett bevezetnem verziókezelőbe. 2013 ide vagy oda, a sorvégek még mindíg gondot tudnak okozni a közös munka folyamán.
Ilyen esetben megoldási lehetőség a verziókezelő megfelelő beállítása, amelyben el lehet érni, hogy adott dokumentumokat milyen szabályok teljesülése esetén fogadjon el. Tehát a forrás nem tartalmazhat tabulátort, windows-os sorvéget.

Végülis azt a megoldást választottam, hogy a kódot magam mentesítem a windows-os (Carriage Return/Line Feed [CR/LF]) és macintosh (Carriage Return [CR]) sorvégektől és egységesen a linux sorvéget (single Line Feed [LF]) használok, valamint ezt írom elő a többi fejlesztőnek is. Tény, hogy így nem garantálhatom, hogy ne tudjanak ettől eltérő kódót a tárolóban rögzíteni.

Windows és Apple környezetben számos megoldás létezik a sorvégek cseréjére. Ezeket azonban nem vágom be ide, mivel azok működőképességét nem tudom ellenőrizni.

Évekkel ezelőtt Debian alatt a dos2unix parancsot használtam. Mint kiderült, ez már nem elérhető az újabb Ubuntu rendszerek alatt. Helyette a tofrodos csomag tartalmazza a fromdos parancsot, de ugyanígy használhatjuk a flip parancsot is.
<pre>
$ sudo apt-get install tofrodos
</pre>
<pre>
$ sudo apt-get install flip
</pre>

ezeket végső soron rá lehet linkelni a régről megszokott parancsra:
<pre>
$ sudo ln -s /usr/bin/fromdos /usr/bin/dos2unix
</pre>
<pre>
$ sudo ln -s /usr/bin/todos /usr/bin/unix2dos
</pre>

A történet itt véget is érhetne, amennyiben az embernek egyszeri, vagy maximum egy könyvtárban található állományokbanban kellene lecserélnie a sorvégeket. Ha azonban adott egy összetett könyvtárstruktúra, amelyben több tízezer forráskód található, vegyesen bináris állományokkal,..
Adódik a válasz, hogy készítsünk egy bash scriptet, ami végigszalad a struktúrán és mindegyik nem bináris állományon lefuttatja a fromdos, vagy a flip megfelelően paraméterezett parancsokat. Ez ügyben Kecsi remélem egy hozzászolásban megosztja a megfelelő megoldást, mert az általam talált bash scriptek nem szuperáltak valami jól és végül nem vacakoltam velük.

Ha már úgyis parancssor, a figyelmem az egysorba tömöríthető parancsok felé terelődött. Némi keresgélés és állítgatás után a következő megoldást találtam, ami tökéletesen megoldotta a problémát:
<pre>
find . -type f -regextype posix-awk -regex "(.*.php)" -exec sed -i s/\\r//g {} ';'
</pre>

<strong>kifejtése:</strong>
<em>find . -type f</em>: az aktuális könyvtárban állva kilistázza az összes alkönyvtár összes állományát, kivéve a könyvtárakat
<em>-regextype posix-awk -regex "(.*.php)"</em>: ezek közül mintaillesztéssel csak a .php kiterjesztésű állományok kiválogatása
<em>-exec sed -i s/\\r//g</em>: carriage return cseréje sed-el
<em>{} ';'</em>: a find parancs által előállt állománylista paraméterként való átadása a sed-nek.
