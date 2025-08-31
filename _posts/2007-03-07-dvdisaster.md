---
excerpt: Már mindenki reflexből ír CD-t és DVD-t. Sokan nem is sejtik, hogy a megírt
  lemez nem lesz hosszú életű. Ennek oka rengeteg minden lehet, mint például a túl
  nagy írási sebesség, a rossz minőségű lemez vagy éppen a rossz minőségű író. Gyakori
  hiba, hogy túl gyors írási sebességet választanak a lemez írásához, így a lemez
  adathordozó felületén (mely egy fémötvözet felgőzölésével keletkezik) létrejövő
  mikroszkopikus lyukak nem megfelelően alakulnak ki.
categories: []
layout: blog
author: sanya
mail: snagy.sandor@gmail.com
title: DVDisaster
created: 1173263474
---
Már mindenki reflexből ír CD-t és DVD-t. Sokan nem is sejtik, hogy a megírt lemez nem lesz hosszú életű. Ennek oka rengeteg minden lehet, mint például a túl nagy írási sebesség, a rossz minőségű lemez vagy éppen a rossz minőségű író. Gyakori hiba, hogy túl gyors írási sebességet választanak a lemez írásához, így a lemez adathordozó felületén (mely egy fémötvözet felgőzölésével keletkezik) létrejövő mikroszkopikus lyukak nem megfelelően alakulnak ki. A tükröző rétegről így nem megfelelő a fényvisszaverődés, ezáltal az olvasás bizonytalanná válik. Az ilyen hibák javítására találták ki a paritásbitet. Sajnos részben a mai sorozatgyártás miatt és részben a meglévő technológia hibái miatt gyakori a lemezeken tárolt adatok elvesztése. (Nem szeretnék kitérni arra, hogy hány évet bírnak ki a mai lemezek és ennek kimerítő indoklására, mert komoly vitákat váltana ki és jelen esetben számomra az adatok biztonságának megőrzése a cél.) A DVDisaster nevű kisméretű alkalmazás képes a lemez hibás részeinek felderítésére, ezzel segítve az adatok megmentését. DVD lemezek esetén képes a PI és PO hibák megszámlálására, melynek feltétele a megfelelő hardver, mely támogatja ezt a funkciót. (Ilyenek az újabb gyártású NEC meghajtók.) A lemezekről készíthetünk iso fájlt illetve lehetőségünk van egy ecc kiterjesztésű fájl készítésére, mellyel pár év múlva esélyünk lesz az időközben megsérült lemez helyreállítására. (Ez utobbi állításomban nem vagyok teljesen biztos, mivel egy korábbi Windows-osoknak szóló cikkben olvastam és még nem nyílt alkalmam a kipróbálásra.) A lemez ellenőrzését a scan gombbal indíthatjuk el. Az elkészülő grafikonon látható a lemez adott részéhez tartozó olvasási sebesség, melynél egy fontos aranyszabály van: csak minimális ingadozások lehetnek egy jó lemeznél. Ha nagy ingadozások történek az arra utal, hogy a meghajtó a paritásbitek segítségével állította helyre az adatfolyamot. Lemezírásnál így arra kell törekedni, hogy az elkészülő lemez ellenőrzésénél minél szebb legyen a grafikon. Ezt úgy lehet elérni, hogy saját tesztekkel megtaláljuk az írónk és a lemezünk számára ideális beállítást. Az így készült lemezek élettartama lesz a legjobb.

A program megtalálható az alap Ubuntu tárolokban!
Weboldal: <a href=http://dvdisaster.sourceforge.net/en/>http://dvdisaster.sourceforge.net/en/</a>
