---
excerpt: "# Látogassunk el az alábbi weboldalra: ''http://www.thawte.com/secure-email/personal-email-certificates/index.html?click=main-nav-products-email#''
  és kattintsunk a '''Click here''' szövegre a lap alján\r\n# Olvassuk el „''Felhasználói
  feltételeket''” a megnyíló ablak közepén. Ha megértettük és elfogadjuk őket, kattintsunk
  a '''next''' gombra. "
categories:
- linux
layout: story
author: szimszon
title: Tanúsítvány beszerzése Firefox böngészővel Thawte-től lépésről lépésre
created: 1215092533
---
# Látogassunk el az alábbi weboldalra: ''http://www.thawte.com/secure-email/personal-email-certificates/index.html?click=main-nav-products-email#'' és kattintsunk a '''Click here''' szövegre a lap alján
# Olvassuk el „''Felhasználói feltételeket''” a megnyíló ablak közepén. Ha megértettük és elfogadjuk őket, kattintsunk a '''next''' gombra. <br>http://linuxbox.hu/sites/default/files/step1.png
# Majd
#* Állítsuk be a '''Charset For Text Input: UTF-8''' -at
#* '''Surname or Family Name:''' Családnév (ékezetet nem szereti)
#* '''First Names or Given Names:''' Keresztnév (ékezetet nem szereti)
#* '''Date Of Birth:''' Születési dátum (nap-hónap-év)
#* '''Nationality:''' Nemzetiség
#* Ha mindent kitöltöttünk kattintsunk a '''next''' gombra <br>http://linuxbox.hu/sites/default/files/step2.png
# '''Email Address/thawte Username:''' az igénylő e-mail címe és egyben a thawte felhasználói neve. Ha kitöltöttük kattintsunk a '''next''' gombra. <br> http://linuxbox.hu/sites/default/files/step3.png
# Lépjünk tovább a '''next''' gombbal<br> http://linuxbox.hu/sites/default/files/step4.png
# A következő oldalon
#* '''Personal Password:''' írjuk be a jelszót
#* '''Confirm Password:''' írjuk be mégegyszer, majd kattintsunk a '''next''' gombra.<br> http://linuxbox.hu/sites/default/files/step5.png
# Itt különböző kérdésekhez különböző válaszokat adhatunk meg arra az esetre, ha elfelejtenénk a jelszavunkat. Beléphetünk a rendszerbe ha az általunk kiválasztott kérdésekre a megfelelő válaszokat adjuk. '''5''' kérdést és választ kell megadni. Érdemes lehet kinyomtatni a lapot ('''print this page''') Továbblépni a '''next'''-re kattintással tudunk.<br>http://linuxbox.hu/sites/default/files/step6.png
# Az oldalon ellenőrizzük le a megadott adatokat, és ha minden rendben van, nyomjuk meg a '''next''' gombot<br> http://linuxbox.hu/sites/default/files/step7.png
# Kapni fogunk egy e-mail-t, amivel életbe lehet léptetni a frissen létrehozott felhasználónkat. (A felugró ablakot bezárhatjuk és várjuk a levelet) <br>http://linuxbox.hu/sites/default/files/step8.png
# A levélben kapott címre menjünk el (kattintsunk rá): https://www.thawte.com/cgi/enroll/personal/step8.exe <br>http://linuxbox.hu/sites/default/files/step9.png
# Szintén a levélben kapott '''Probe:''' és '''Ping:''' számokat és betűket másoljuk a weboldal megfelelő mezőjébe<br> http://linuxbox.hu/sites/default/files/step10.png
# Ha a felhasználó létrehozása sikerült a '''next''' gombbal be tudunk lépni<br> http://linuxbox.hu/sites/default/files/step11.png
# A következő oldalon kicsit ki kell bővíteni a magunkról megadott adatokat: https://www.thawte.com/cgi/personal/general/editinfo.exe <br>http://linuxbox.hu/sites/default/files/step12.png <br>Itt a névben már be lehet írni ékezetes betűket, a 
#*'''Hungarian National Identification Number'''-hez legjobb, ha a jogosítvány vagy útlevél számát adjuk meg, vagy valami állami fényképes igazolvány számát
#* '''National Identity Type:''' -hoz írjuk be, hogy a felette megadott szám milyen igazolványhoz tartozik. Pl.: ''Driver's license'' (jogosítvány) <br> majd kattintsunk az '''Update''' gombra
# https://www.thawte.com/cgi/personal/wot/directory.exe?node=10765 oldalon keressünk hitelesítőt a környékünkön és a weblapon látható e-mail címen vegyük fel vele a kapcsolatot. Ha tudunk vele találkozni engedélyezzük a kiválasztottnak, hogy lássa az adatainkat: '''Allow <hitelesítő neve> to view your details'''. <br>http://linuxbox.hu/sites/default/files/step13.png
# Addig is amíg összeszedjük az '''50''' pontot, készíthetünk tanúsítványt, még a nevünk nélkül a https://www.thawte.com/cgi/personal/cert/enroll.exe oldalon a '''Request''' gombra kattintva<br> http://linuxbox.hu/sites/default/files/step14.png
# Válasszuk ki a böngészőnk típusát és kattintsunk a  '''Request'''-re<br> http://linuxbox.hu/sites/default/files/step15.png
# Lépjünk tovább: '''next'''<br> http://linuxbox.hu/sites/default/files/step16.png
# Lehetőleg, ha több is van, csak egy e-mail címet válasszunk ki<br> http://linuxbox.hu/sites/default/files/step17.png
# Lépjünk tovább: '''next'''<br> http://linuxbox.hu/sites/default/files/step18.png
# Lépjünk tovább: '''accept'''<br> http://linuxbox.hu/sites/default/files/step19.png
# Lépjünk tovább: '''next'''<br> http://linuxbox.hu/sites/default/files/step20.png
# Lépjünk tovább: '''finish'''<br> http://linuxbox.hu/sites/default/files/step21.png
# Ezután az ablak bezárható, és egy kis időt várni kell amíg megjelenik az igényelt tanúsítvány
# https://www.thawte.com/cgi/personal/cert/status.exe oldalon megtaláljuk az eddig legyártott tanúsítványokat<br>'''Navigator:''' -ra kattintva megnézhetjük a tulajdonságait<br> http://linuxbox.hu/sites/default/files/step22.png
# A '''fetch''' gombra kattintva telepíthetjük a böngészőnkbe a tanúsítványt<br> http://linuxbox.hu/sites/default/files/step23.png
# Készítsünk biztonsági másolatot a kulcsról. A bőngésző menüjéből '''Szerkesztés''' vagy '''Eszközök''' -> '''Beállítások''' -> '''Haladó''' -> '''Titkosítás''' -> '''Tanúsítványkezelő''' -> '''Mentés'''. Ha meg van adva mesterjelszó, akkor a böngésző először bekéri, majd a kimentett tanúsítványt titkosítja egy jelszóval amit tőlünk kérdez meg. <br>http://linuxbox.hu/sites/default/files/step24.png
# Az elmentett tanúsítványt már betölthetjük a levelező programunkba: [http://linuxbox.hu/node/532 Tanúsítvány használata Thunderbird levelező programmal lépésről lépésre], [http://linuxbox.hu/node/533 Tanúsítvány használata Horde webmaillel lépésről lépésre]
