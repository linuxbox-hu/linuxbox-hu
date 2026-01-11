---
excerpt: "== Telepítés ==\r\n\r\nMiután [http://linuxbox.hu/node/531 Beszereztük a
  Tanúsítványt Firefox-szal a Thawte-től lépésről lépésre], már be is importálhatjuk
  a levelező programunkba.\r\n"
categories:
- linux
layout: story
author: szimszon
title: Tanúsítvány használata Horde webmaillel lépésről lépésre
created: 1215181160
---
== Telepítés ==

Miután [http://linuxbox.hu/node/531 Beszereztük a Tanúsítványt Firefox-szal a Thawte-től lépésről lépésre], már be is importálhatjuk a levelező programunkba.
<!--break-->
# A menüből válasszuk az '''Opciók''' -> '''Levelezés'''-t <br>http://linuxbox.hu/sites/default/files/hstep1.png<br>, majd az '''S/MIME beállítások''' linket<br>http://linuxbox.hu/sites/default/files/hstep2.png, amennyiben nincs, fel kell vennünk a kapcsolatot a weboldal üzemeltetőjével, hogy kapcsolja be ezt a funkciót.
# Kapcsoljuk be ezt a lehetőséget:<br>http://linuxbox.hu/sites/default/files/hstep3.png
# Kattintsunk a '''Kulcspár importálása'''-ra:<br>http://linuxbox.hu/sites/default/files/hstep4.png 
# A '''Feltöltés''' sorban a '''Tallózás...'''-ra kattintva keressük ki az elmentett tanúsítványunkat, majd írjuk be a '''Jelszó'''t amivel a tanúsítványt védtük a lementéskor és adjuk meg '''A titkos kulcs jelszava'''t, amivel a tanúsítványunkat a weboldalon védjük majd:<br>http://linuxbox.hu/sites/default/files/hstep5.png<br>Majd '''Kulcs importálása''' 
# Ezzel a kulcsot telepítettük.

== A tanúsítvány felhasználása a levelezésben ==

A weboldal ha egyszer már bekérte a jelszót a tanúsítványhoz akkor kilépésig nem fogja újra kérni tőlünk, így figyeljünk oda, hogy gépünkhöz illetéktelen ne férhessen hozzá, ugyanis levelet tud küldeni a nevünkben a mi aláírásunkkal.

=== Levél küldése digitális aláírással ===

# '''Új levél'''<br>http://linuxbox.hu/sites/default/files/hstep6.png
# Ellenőrizzük a titkosítási beállításokat:<br>http://linuxbox.hu/sites/default/files/hstep7.png
# Majd kattintsunk a '''Küldjük el'''-re.
#* Ha egy felugró ablakot kapunk, akkor oda írjuk be a jelszót amivel a tanúsítványt védjük:<br>http://linuxbox.hu/sites/default/files/hstep8.png<br>és a levél el is ment...

=== Digitális aláírással ellátott levél fogadása ===

Ha árlépünk egy levélre, akkor valami hasonlónak kell fogadni minket:<br>http://linuxbox.hu/sites/default/files/hstep9.png<br>ez jelzi, hogy az üzenetet aláírták.

=== Titkosított (digitálisan aláírt) levél küldése ===

Ahhoz, hogy titkosított levelet tudjunk küldeni egy címzettnek, ahhoz a címzettnek szerepelnie kell a címlistánkban a saját nyilvános tanúsítványával együtt. A legegyszerűbb, ha kérünk tőle egy digitálisan aláírt levelet.
# Vegyük fel a címlistánkba, ha még nem szerepel<br>http://linuxbox.hu/sites/default/files/hstep10.png
# Ha szerencsénk van akkor a levélben az S/MIME résznél megjelenik egy harmadik sor, amiben szerepel a '''Mentsük el a címjegyzékben''' szöveg.<br>http://linuxbox.hu/sites/default/files/hstep11.png<br>, ezzel felvettük a címzett nyilvános tanúsítványát a címjegyzékbe, és titkosítva tudunk neki üzenetet küldeni
# '''Új levél'''<br>http://linuxbox.hu/sites/default/files/hstep6.png
# Ellenőrizzük a titkosítási beállításokat:<br>http://linuxbox.hu/sites/default/files/hstep12.png
# Majd kattintsunk a '''Küldjük el'''-re.
#* Ha egy felugró ablakot kapunk, akkor oda írjuk be a jelszót amivel a tanúsítványt védjük:<br>http://linuxbox.hu/sites/default/files/hstep8.png<br>és a levél el is ment...

=== Titkosított levél fogadása ===

Szinte teljesen megegyezik a digitális aláírással küldött levél fogadásával, csak van egy plusz sor, ami elírja, hogy az üzenet titkosítva érkezett.<br>http://linuxbox.hu/sites/default/files/hstep13.png
