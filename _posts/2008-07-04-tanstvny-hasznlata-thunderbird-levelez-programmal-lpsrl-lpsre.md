---
excerpt: "== Telepítés ==\r\n\r\nMiután [http://linuxbox.hu/node/531 Beszereztük a
  Tanúsítványt Firefox-szal a Thawte-től lépésről lépésre], már be is importálhatjuk
  a levelező programunkba.\r\n"
categories:
- linux
layout: story
author: szimszon
title: Tanúsítvány használata Thunderbird levelező programmal lépésről lépésre
created: 1215172641
---
== Telepítés ==

Miután [http://linuxbox.hu/node/531 Beszereztük a Tanúsítványt Firefox-szal a Thawte-től lépésről lépésre], már be is importálhatjuk a levelező programunkba.
<!--break-->
# A program menüjéből válasszuk ki a '''Szerkesztés''' vagy '''Eszközök''' -> '''Beállítások''' -> '''Haladó''' -> '''Tanúsítványok''' -> '''Tanúsítványok megjelenítése''' lehetőséget. <br> http://linuxbox.hu/sites/default/files/kstep1.png<br> Ezzel beléptünk a ''Tanúsítványkezelőbe'', itt klikkeljünk az '''Importálás''' gombra. A felbukkanó ablakban keressük ki az előzőleg megszerzett és elmentett tanúsítványt. Majd kattintsunk az '''OK''' gombra.
# Ha  ''Mesterjelszót'' is beállítottunk (ajánlott) a rendszerbe, akkor azt itt meg fogja kérdezni<br>http://linuxbox.hu/sites/default/files/kstep2.png<br>Írjuk be.
# Ez után a következő ablak meg fogja kérdezni, hogy az elmentett tanúsítványt milyen jelszóval védtük.<br>http://linuxbox.hu/sites/default/files/kstep3.png<br>Írjuk be, majd '''OK'''.<br>http://linuxbox.hu/sites/default/files/kstep4.png<br>'''OK''', ezzel a tanúsítványt telepítettük.

== Előkészítés a használatra ==

# A menükből keressük ki a '''Szerkesztés''' -> '''Postafiókok beállításai'''-t.<br>http://linuxbox.hu/sites/default/files/kstep5.png
# Válasszuk ki a beállított postafiókok közül azt amelyiknél a tanúsítványt fel akarjuk használni, és ott válasszuk ki a '''Biztonság''' menüpontot<br>http://linuxbox.hu/sites/default/files/kstep6.png
# A megjelenő lapon a ''Digitális aláírás'' résznél<br>http://linuxbox.hu/sites/default/files/kstep7.png<br> kattintsunk a '''Kiválasztás''' gombra. A megjelenő '''Tanúsítvány kiválasztása''' ablakban<br>http://linuxbox.hu/sites/default/files/kstep8.png<br> a '''Tanúsítvány:''' sor lenyíló menüjéből válasszuk ki a frissen importált tanúsítványunkat, majd nyomjunk az '''OK''' gombra.<br>A felbukkanő ablak kérését fogadjuk el<br>http://linuxbox.hu/sites/default/files/kstep9.png<br>ezzel ugyanis egyből beállíthatjuk azt a tanúsítványt amivel ha nekünk küldenek üzenetet, akkor azt titkosítani tudják számunkra. Az '''Üzenetek digitális aláírása''' elé tegyünk egy pipát (vagy ''X''-et). Ezzel kiválasztottuk azt a tanúsítványt amivel a leveleinket digitálisan alá szeretnénk írni.
# A '''Postafiók beállításai''' ablak alján lévő '''OK''' gombot nyomjuk meg.
# A tanúsítványunk készen áll a használatra.

== A tanúsítvány felhasználása a levelezésben ==

A tanúsítványok kezelésénél a [http://www.mozilla-europe.org/hu/products/thunderbird/ Thunderbird] a saját tanúsítvány kezelőjét használja. A tanúsítványokat egy '''Mester''' jelszóval lehet védeni, amit célszerű alkalmazni.

A program ha egyszer már bekérte ezt a jelszót akkor kikapcsolásáig nem fogja újra kérni tőlünk, így figyeljünk oda, hogy gépünkhöz illetéktelen ne férhessen hozzá, ugyanis levelet tud küldeni a nevünkben a mi aláírásunkkal.

Amennyiben nem használunk '''Mester''' jelszót, úgy a tanúsítványainkhoz is hozzáférhet!

=== Levél küldése digitális aláírással ===

# '''Új üzenet létrehozása'''
# A megjelenő ablakon ellenőrizzük, hogy a jobb sarokban lévő jobbszélső ikon be van-e kapcsolva<br>http://linuxbox.hu/sites/default/files/kstep10.png
# Ha bizonytalanok vagyunk, vagy ha az ikon nem mutat semmit, nézzük meg a ''Feladó:'' fölötti gombok között az '''S/MIME''' gomb lenyíló részén<br>http://linuxbox.hu/sites/default/files/kstep11.png<br>Ha pipa van az '''Üzenet digitális aláírása''' előtt, akkor megnyugodhatunk, mert a kimenő levelünk alá lesz írva.

=== Digitális aláírással ellátott levél fogadása ===

Ha árlépünk egy levélre, akkor egy kis ikon<br>http://linuxbox.hu/sites/default/files/kstep12.png<br>jelzi, hogy az üzenetet aláírták. Ha erre az ikonra kétszer kattintunk akkor megjelenik egy ablak az aláíró tanúsítvány tulajdonságaival.<br>Ha hibás lenne az aláírás akkor az az ikonon is meglátszik<br>http://linuxbox.hu/sites/default/files/kstep14.png

=== Titkosított (digitálisan aláírt) levél küldése ===

Ahhoz hogy a levelet titkosítani tudjuk először be kell szereznünk a címzett nyilvános tanúsítványát. Ennek talán egyik legegyszerűbb módja ha megkérjük, hogy küldjön egy digitálisan aláírt levelet, amibe a nyilvános tanúsítványát is beleteszi.

Ha [http://www.mozilla-europe.org/hu/products/thunderbird/ Thunderbird]-öt használ és az ''Előkészítés a használatra'' -nak megfelelően van beállítva, akkor elég lesz, ha ír nekünk egy digitálisan aláírt e-mail-t. A levelező program automatikusan hozzácsomagolja a tanúsítványt.

Ha a [http://www.mozilla-europe.org/hu/products/thunderbird/ Thunderbird] olyan levéllel találkozik, amiben nyilvános kulcs található, akkor önműködően felveszi a tanúsítványok közé és mi egy kattintással titkosíthatjuk a címzettnek küldendő üzenetünket.<br>http://linuxbox.hu/sites/default/files/kstep15.png

=== Titkosított levél fogadása ===

Kis ikonok fogják jelezni az üzenet titkosításának tényét.<br>http://linuxbox.hu/sites/linuxbox.hufiles/kstep16.png

Illetve ha valami miatt nem lehet visszafejteni a titkosítást, arról a [http://www.mozilla-europe.org/hu/products/thunderbird/ Thunderbird] tájékoztat...<br>http://linuxbox.hu/sites/default/files/kstep17.png

Az ikonokra kétszer kattintva megnézhetjük az aláírás és titkosítás tulajdonságait.
