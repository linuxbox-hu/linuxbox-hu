---
author: szimszon
categories:
- linux
created: 1215172641
date: '2008-07-04T00:00:00Z'
description: |
  == Telepítés ==
  
  Miután [http://linuxbox.hu/node/531 Beszereztük a Tanúsítványt Firefox-szal a Thawte-től lépésről lépésre], már be is importálhatjuk a levelező programunkba.
title: Tanúsítvány használata Thunderbird levelező programmal lépésről lépésre
aliases:
- /node/532/
- /story/532/
---
### Telepítés

Miután [Beszereztük a Tanúsítványt Firefox-szal a Thawte-től lépésről lépésre](/node/531), már be is importálhatjuk a levelező programunkba.

1. A program menüjéből válasszuk ki a **Szerkesztés** vagy **Eszközök** -> **Beállítások** -> **Haladó** -> **Tanúsítványok** -> **Tanúsítványok megjelenítése** lehetőséget.

   ![](/assets/img/posts/kstep1.png)

   Ezzel beléptünk a *Tanúsítványkezelőbe*, itt klikkeljünk az **Importálás** gombra. A felbukkanó ablakban keressük ki az előzőleg megszerzett és elmentett tanúsítványt. Majd kattintsunk az **OK** gombra.
2. Ha *Mesterjelszót* is beállítottunk (ajánlott) a rendszerbe, akkor azt itt meg fogja kérdezni

   ![](/assets/img/posts/kstep2.png)

   Írjuk be.
3. Ez után a következő ablak meg fogja kérdezni, hogy az elmentett tanúsítványt milyen jelszóval védtük.

   ![](/assets/img/posts/kstep3.png)

   Írjuk be, majd **OK**.

   ![](/assets/img/posts/kstep4.png)

   **OK**, ezzel a tanúsítványt telepítettük.

### Előkészítés a használatra

1. A menükből keressük ki a **Szerkesztés** -> **Postafiókok beállításai**-t.

   ![](/assets/img/posts/kstep5.png)
2. Válasszuk ki a beállított postafiókok közül azt amelyiknél a tanúsítványt fel akarjuk használni, és ott válasszuk ki a **Biztonság** menüpontot

   ![](/assets/img/posts/kstep6.png)
3. A megjelenő lapon a *Digitális aláírás* résznél

   ![](/assets/img/posts/kstep7.png)

   kattintsunk a **Kiválasztás** gombra. A megjelenő **Tanúsítvány kiválasztása** ablakban

   ![](/assets/img/posts/kstep8.png)

   a **Tanúsítvány:** sor lenyíló menüjéből válasszuk ki a frissen importált tanúsítványunkat, majd nyomjunk az **OK** gombra. A felbukkanő ablak kérését fogadjuk el

   ![](/assets/img/posts/kstep9.png)

   ezzel ugyanis egyből beállíthatjuk azt a tanúsítványt amivel ha nekünk küldenek üzenetet, akkor azt titkosítani tudják számunkra. Az **Üzenetek digitális aláírása** elé tegyünk egy pipát (vagy *X*-et). Ezzel kiválasztottuk azt a tanúsítványt amivel a leveleinket digitálisan alá szeretnénk írni.
4. A **Postafiók beállításai** ablak alján lévő **OK** gombot nyomjuk meg.
5. A tanúsítványunk készen áll a használatra.

### A tanúsítvány felhasználása a levelezésben

A tanúsítványok kezelésénél a [Thunderbird](http://www.mozilla-europe.org/hu/products/thunderbird/) a saját tanúsítvány kezelőjét használja. A tanúsítványokat egy **Mester** jelszóval lehet védeni, amit célszerű alkalmazni.

A program ha egyszer már bekérte ezt a jelszót akkor kikapcsolásáig nem fogja újra kérni tőlünk, így figyeljünk oda, hogy gépünkhöz illetéktelen ne férhessen hozzá, ugyanis levelet tud küldeni a nevünkben a mi aláírásunkkal.

Amennyiben nem használunk **Mester** jelszót, úgy a tanúsítványainkhoz is hozzáférhet!

#### Levél küldése digitális aláírással

1. **Új üzenet létrehozása**
2. A megjelenő ablakon ellenőrizzük, hogy a jobb sarokban lévő jobbszélső ikon be van-e kapcsolva

   ![](/assets/img/posts/kstep10.png)
3. Ha bizonytalanok vagyunk, vagy ha az ikon nem mutat semmit, nézzük meg a *Feladó:* fölötti gombok között az **S/MIME** gomb lenyíló részén

   ![](/assets/img/posts/kstep11.png)

   Ha pipa van az **Üzenet digitális aláírása** előtt, akkor megnyugodhatunk, mert a kimenő levelünk alá lesz írva.

#### Digitális aláírással ellátott levél fogadása

Ha árlépünk egy levélre, akkor egy kis ikon

![](/assets/img/posts/kstep12.png)

jelzi, hogy az üzenetet aláírták. Ha erre az ikonra kétszer kattintunk akkor megjelenik egy ablak az aláíró tanúsítvány tulajdonságaival.

Ha hibás lenne az aláírás akkor az az ikonon is meglátszik

![](/assets/img/posts/kstep14.png)

#### Titkosított (digitálisan aláírt) levél küldése

Ahhoz hogy a levelet titkosítani tudjuk először be kell szereznünk a címzett nyilvános tanúsítványát. Ennek talán egyik legegyszerűbb módja ha megkérjük, hogy küldjön egy digitálisan aláírt levelet, amibe a nyilvános tanúsítványát is beleteszi.

Ha [Thunderbird](http://www.mozilla-europe.org/hu/products/thunderbird/)-öt használ és az *Előkészítés a használatra* -nak megfelelően van beállítva, akkor elég lesz, ha ír nekünk egy digitálisan aláírt e-mail-t. A levelező program automatikusan hozzácsomagolja a tanúsítványt.

Ha a [Thunderbird](http://www.mozilla-europe.org/hu/products/thunderbird/) olyan levéllel találkozik, amiben nyilvános kulcs található, akkor önműködően felveszi a tanúsítványok közé és mi egy kattintással titkosíthatjuk a címzettnek küldendő üzenetünket.

![](/assets/img/posts/kstep15.png)

#### Titkosított levél fogadása

Kis ikonok fogják jelezni az üzenet titkosításának tényét.

![](/assets/img/posts/kstep16.png)

Illetve ha valami miatt nem lehet visszafejteni a titkosítást, arról a [Thunderbird](http://www.mozilla-europe.org/hu/products/thunderbird/) tájékoztat...

![](/assets/img/posts/kstep17.png)

Az ikonokra kétszer kattintva megnézhetjük az aláírás és titkosítás tulajdonságait.
