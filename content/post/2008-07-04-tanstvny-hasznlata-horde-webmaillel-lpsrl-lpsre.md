---
author: szimszon
categories:
- linux
created: 1215181160
date: '2008-07-04T00:00:00Z'
description: |
  == Telepítés ==
  
  Miután [http://linuxbox.hu/node/531 Beszereztük a Tanúsítványt Firefox-szal a Thawte-től lépésről lépésre], már be is importálhatjuk a levelező programunkba.
title: Tanúsítvány használata Horde webmaillel lépésről lépésre
aliases:
- /node/533/
- /story/533/
---
### Telepítés

Miután [Beszereztük a Tanúsítványt Firefox-szal a Thawte-től lépésről lépésre](/node/531), már be is importálhatjuk a levelező programunkba.

1. A menüből válasszuk az **Opciók** -> **Levelezés**-t

   ![](/assets/img/posts/hstep1.png)

   , majd az **S/MIME beállítások** linket

   ![](/assets/img/posts/hstep2.png)

   , amennyiben nincs, fel kell vennünk a kapcsolatot a weboldal üzemeltetőjével, hogy kapcsolja be ezt a funkciót.
2. Kapcsoljuk be ezt a lehetőséget:

   ![](/assets/img/posts/hstep3.png)
3. Kattintsunk a **Kulcspár importálása**-ra:

   ![](/assets/img/posts/hstep4.png)
4. A **Feltöltés** sorban a **Tallózás...**-ra kattintva keressük ki az elmentett tanúsítványunkat, majd írjuk be a **Jelszó**t amivel a tanúsítványt védtük a lementéskor és adjuk meg **A titkos kulcs jelszava**t, amivel a tanúsítványunkat a weboldalon védjük majd:

   ![](/assets/img/posts/hstep5.png)

   Majd **Kulcs importálása**
5. Ezzel a kulcsot telepítettük.

### A tanúsítvány felhasználása a levelezésben

A weboldal ha egyszer már bekérte a jelszót a tanúsítványhoz akkor kilépésig nem fogja újra kérni tőlünk, így figyeljünk oda, hogy gépünkhöz illetéktelen ne férhessen hozzá, ugyanis levelet tud küldeni a nevünkben a mi aláírásunkkal.

#### Levél küldése digitális aláírással

1. **Új levél**

   ![](/assets/img/posts/hstep6.png)
2. Ellenőrizzük a titkosítási beállításokat:

   ![](/assets/img/posts/hstep7.png)
3. Majd kattintsunk a **Küldjük el**-re.
   - Ha egy felugró ablakot kapunk, akkor oda írjuk be a jelszót amivel a tanúsítványt védjük:

     ![](/assets/img/posts/hstep8.png)

     és a levél el is ment...

#### Digitális aláírással ellátott levél fogadása

Ha árlépünk egy levélre, akkor valami hasonlónak kell fogadni minket:

![](/assets/img/posts/hstep9.png)

ez jelzi, hogy az üzenetet aláírták.

#### Titkosított (digitálisan aláírt) levél küldése

Ahhoz, hogy titkosított levelet tudjunk küldeni egy címzettnek, ahhoz a címzettnek szerepelnie kell a címlistánkban a saját nyilvános tanúsítványával együtt. A legegyszerűbb, ha kérünk tőle egy digitálisan aláírt levelet.

1. Vegyük fel a címlistánkba, ha még nem szerepel

   ![](/assets/img/posts/hstep10.png)
2. Ha szerencsénk van akkor a levélben az S/MIME résznél megjelenik egy harmadik sor, amiben szerepel a **Mentsük el a címjegyzékben** szöveg.

   ![](/assets/img/posts/hstep11.png)

   , ezzel felvettük a címzett nyilvános tanúsítványát a címjegyzékbe, és titkosítva tudunk neki üzenetet küldeni
3. **Új levél**

   ![](/assets/img/posts/hstep6.png)
4. Ellenőrizzük a titkosítási beállításokat:

   ![](/assets/img/posts/hstep12.png)
5. Majd kattintsunk a **Küldjük el**-re.
   - Ha egy felugró ablakot kapunk, akkor oda írjuk be a jelszót amivel a tanúsítványt védjük:

     ![](/assets/img/posts/hstep8.png)

     és a levél el is ment...

#### Titkosított levél fogadása

Szinte teljesen megegyezik a digitális aláírással küldött levél fogadásával, csak van egy plusz sor, ami elírja, hogy az üzenet titkosítva érkezett.

![](/assets/img/posts/hstep13.png)
