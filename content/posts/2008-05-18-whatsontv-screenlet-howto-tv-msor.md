---
author: ricsi-pontaz
categories:
- ubuntu
created: 1211118287
date: '2008-05-18T00:00:00Z'
excerpt: 'Amióta Hardyn nem igazán akarnak működni a TV műsoros RSS olvasók, vagy nekem nem tetszenek, elkezdtem keresgélni valami más alternatíva után. Meg is lett:
  WhatsOnTV Screenlet: Képernyőkép. Maximálisan 20 csatorna műsorát láthatjuk a képernyőnkön, az egyetlen negatívum, hogy csatornánként csak az éppen aktuális és az utána következő müsort mutatja.'
title: WhatsOnTV Screenlet HowTo (TV müsor)
aliases:
- /node/514/
- /story/514/
---
Amióta Hardyn nem igazán akarnak működni a TV műsoros RSS olvasók, vagy nekem nem tetszenek, elkezdtem keresgélni valami más alternatíva után. Meg is lett:

WhatsOnTV Screenlet: [Képernyőkép](http://kepfeltolto.hu/i/?102116)

Maximálisan 20 csatorna műsorát láthatjuk a képernyőnkön, az egyetlen negatívum, hogy csatornánként csak az éppen aktuális és az utána következő müsort mutatja. Itt kérnék segítséget, ha valaki ismeri a python nyelvet átírhatná, hogy 5 műsort mutasson csatornánként. :)

Segítség az üzembehelyezéshez:
**A következő parancsoknál értelemszerűen módosítsd a *felhasználónév* mappát a saját mappád nevére.**

Először is ha valakinek nem lenne fent a Screenlets az innen telepítheti (ubuntu-deb csomag, szóval csak kattintgatni kell)
[http://www.getdeb.net/app/Screenlets](http://www.getdeb.net/app/Screenlets) vagy telepítheti `sudo aptitude install screenlets` segítségével.

Majd töltsük le magát a WhatsOnTV screenlet-et, ezt ezen a linken tehetjük meg:
[http://www.mediafire.com/?bgrdw1vg4lj](http://www.mediafire.com/?bgrdw1vg4lj)

Indítsuk el a Screenlets-et, terminálba kiadjuk a

`screenlets-manager`

parancsot.

Majd a WhatsOnTV.tar.gz fájlt csak úgy húzzuk bele a Screenlets Managerbe, ennek következményeképpen fel is települ. Keressük meg a listából, majd dupla kattintással helyezzük az asztalra. (Nem kell megijedni, hogy hibát jelez: No XMLTV data found, ez itt még természetes)
A Screenlets Managerbe kattintsunk erre a screenletsre majd bal oldalt van egy olyan pipálható opció, hogy Auto start on login, ez azért jó, hogy mikor bejelentkezünk automatikusan induljon el.

Majd telepítsük az XMLTV-t, hogy legyen majd műsorunk:

`sudo aptitude install xmltv`

Majd leszedjük a műsorújságokat:

`tv_find_grabbers`

Majd be állítjuk a magyar csatornák közül, hogy melyikeket szeretnék majd megjeleníteni:

`sudo tv_grab_huro --configure`

Mivel a magyar és román csatornák együtt vannak, ezért válasszuk, hogy nekünk csak a magyar csatornák kellenek:

írjuk be `Hungary`.

Erre egyesével elkezdi megkérdezni, hogy melyik csatornák kellenek. Először az m1-et kérdi. Ha szeretnék majd megjeleníteni akkor adjuk ki a yes parancsot, ha nem akkor no.
Majd kérdi az m2-t. Itt is válasszunk és így tovább. Ha már kiválasztottuk mindet ami nekünk kell, adjuk ki a none parancsot akkor az összes többire no-val fog válaszolni. Ellenkező esetben végig nézhetjük az egész listát. Nem olyan sok.

Erre kaptunk egy .xmltv könyvtárat a saját mappánkba, benne egy konfig fájlal amely tartalmazza, hogy melyik csatornák kellenek a későbbiekben.

Rendben akkor most töltsünk le egy XML fájlt a következő képpen:

`sudo tv_grab_huro --output=/home/felhasznalonev/.xmltv/musor.xml`

Ez kicsit tovább tart, várjuk ki.

Ezután rendezzük a fájl tartalmát, hogy képes legyen a program megjeleníteni:

`sudo tv_sort --output=/home/felhasznalonev/.xmltv/musor.xml /home/felhasznalonev/.xmltv/musor.xml`

Ha ez kész kattintsunk jobb gombbal a screenletre, options, majd settings. És ott állítsuk be WhatsOnTVScreenlet/XMLTV file path-nál a musor.xml fájlt. Majd ismét jobb gomb a screenletre és Refresh Data.
Ha mindent jól csináltuk már meg kell jelennie a műsornak. Most TV logókat varázsolunk mellé. Van egy olyan opciója a screenletnek, hogy download logo, azaz logók letöltése, de nálam nem működik, gondolom, hogy csak ismertebb csatornákkal használható. Na mindegy, állítunk be mi logót kézileg. Köszönet `wuuk23`-nak aki elkészítette 98 magyar csatorna logóját, persze ha valakinek vannak más igényei, egy-két szóból lehet csinálni új logókat.

Na szóval innen érhetitek el wuuk23 logó packját:
[http://data.hu/get/277976/logos.tar.gz.html](http://data.hu/get/277976/logos.tar.gz.html) vagy [http://www.mediafire.com/?ngnxyvbezyj](http://www.mediafire.com/?ngnxyvbezyj)

Csomagoljuk ki a logókat, majd pedig befogjuk őket másolni a helyükre.
Ami a saját mappádban a .screenlets/WhatsOnTV/logos könyvtár. Ha ide másolod a logókat, akkor azok automatikusan megjelennek. **FONTOS: A logók nevét nem szabad megváltoztatni, mert azok alapján azonosítja a program.** Ha készítesz egy logót akkor a nevét a saját mappádon belül a .xmltv/musor.xml fájlból tudod kinézni. Például a TV2-nél ez a sor azonosítja a nevet:

`channel id="003.port.hu"`

Ezért 003.port.hu.png a logó neve. **Másik fontos kritérium, hogy a logók csak akkor jelennek meg ha PNG formátumúak.**

A nehezén túl vagyunk. Csak az a baj, hogy csak egy napi műsort töltöttünk most le. Ezért elfogjuk érni, hogy az Ubuntu minden indításakor töltse le nekünk a napi műsorokat. Ehhez pedig készítünk egy fájlt, nevezzük el letolt.sh -nak és tegyük a saját mappánkon belül az .xmltv könyvtárba.

A tartalma a következő legyen:

```bash
tv_grab_huro --output=/home/felhasznalonev/.xmltv/musor.xml

tv_sort --output=/home/felhasznalonev/.xmltv/musor.xml /home/felhasznalonev/.xmltv/musor.xml
```

Most pedig beállítjuk, hogy minden indításkor fusson le ez a fájl.
Válasszuk a Rendszer menüt, majd azon belül az Adminisztrációt, és ott a Munkameneteket. Hozzáadásra kattintsunk, név bármi lehet, én azt adtam meg, hogy: TV müsor letöltése, parancs: sh /home/felhasznalonev/.xmltv/letolt.sh

Majd pedig írás jogot kell adnunk két fájlnak, a saját mappánkban az .xmltv/supplement/tv_grab_huro/jobmap.meta és a catmap.hu.meta

(Én ezt a következőképpen teszem, terminálba gksu gnome-commander, erre a parancsra rootként megjeleníti a gnome-commander, persze ehhez szükséges, hogy telepítve legyen, ha nincs, sudo aptitude install gnome-commander. Ha ez meg van keressük meg a fájlokat, majd jelöljük ki, fájl menü/jogok módosítása, azon belül adjunk a "Többeknek" írás jogot)

Ezzel készen is vagyunk. Mikor bejelentkezünk elkezdi letölteni az aktuális TV műsort, ez kicsit hosszabb idő, szóval legyünk türelmesek rendszer indításkor, körülbelül 2 percet vesz igénybe mire letölti a program a műsort. Utána kattintsunk jobb gombbal, majd Refresh Data, ha nem akarjuk kivárni még a program automatikusan frissíti magát.

Ha bárhol megakadtál írj csak nyugodtan, megpróbálok segíteni. :)
