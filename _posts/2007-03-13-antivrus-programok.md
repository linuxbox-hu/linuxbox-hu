---
excerpt: Már régóta szerettem volna egy antivírus programot az Ubuntu-mra telepíteni,
  de a biztonságérzetem miatt ez mostanáig elhúzódott. Elvileg Linux alatt kevés vírus
  létezik, így inkább a rendszer feltörésétől kell jobban félni. Keresgélésem olyan
  szoftverre irányult, mely nem található meg az alap Ubuntu tárolók közt. Alap esetben
  könnyen telepíthető a clamav és a KDE-s kezelőfelülete, a klamav.
categories: []
layout: blog
author: sanya
title: Antivírus programok
created: 1173785871
---
Már régóta szerettem volna egy antivírus programot az Ubuntu-mra telepíteni, de a biztonságérzetem miatt ez mostanáig elhúzódott. Elvileg Linux alatt kevés vírus létezik, így inkább a rendszer feltörésétől kell jobban félni. Keresgélésem olyan szoftverre irányult, mely nem található meg az alap Ubuntu tárolók közt. Alap esetben könnyen telepíthető a clamav és a KDE-s kezelőfelülete, a klamav. Biztos vagyok benne, hogy ez is nagyon jó, de engem a havp (http forgalmat ellenőrző démon) hibás feltelepülése felmérgesített és elkezdtem keresgélni másik víruskeresőt.

1. Avast

Először az Avast-ot próbáltam ki, mivel ezt lehetett a legegyszerűbben telepíteni. Programot az <a href=http://www.avast.com/eng/download-avast-for-linux-edition.html>Avast</a> honlapjáról lehet letölteni (rpm, deb és forrás változatban). A Home edition ingyenesen használható csak regisztrációra van szükség. Szerencsére a regisztráció első kérdése a nyelv kiválasztás, melyet ha magyarra állítunk, akkor az egész oldal magyarnyelvű lesz! Regisztráció után kapunk egy e-mail-t, melyben megtalálható a regisztrációs kódunk.
A program telepítése egyszerű, két utasítást kell konzolon kiadni:
sudo dpkg -i avast4workstation_1.0.6-2_i386.deb (a program telepítése)
sudo /usr/lib/avast4workstation/share/avast/desktop/install-desktop-entries.sh install (az indító ikon elhelyezése a menűbe)
Az első indításnál be kell másolni a regisztrációs kódot, mely után érdemes a kezelőfelületen az adatbázis frissítését kérni az Update database gombbal. A kezelőfelület olyan egyszerű, hogy külön kommentárt felesleges írnom.

2. AVG

Az <a href=http://www.avg.hu>AVG</a> weboldalán rengeteg lehetőséget találunk, de csak egy ingyenes Linux változat van. (Fizetős változat is létezik Linuxra, mely démon formájában fut a háttérben.) Letöltésnél sajnos nincs deb csomag, csak rpm. Telepítés ennek megfelelően kis átalakítással kezdődik. Én így csináltam:
sudo alien –c –d avgcsomag.rpm
sudo dpkg –i avgcsomag.deb
Ezzel még nem teljes a telepítés, ha megpróbáljuk a menüből indítani sajnos nem fog működni. Első indítás elött regisztrálni kell parancssorból:
sudo /usr/bin/avgscan -register 70FREE-TX-IB-P1-C01-S139FC-327-9FPB
(Ezt a reg.kódot a weben keresgélve találtam, de a Windows-os verzió telepítésénél megjelenő kód átmásolásával is használhatjuk az Linux-os AVG-t.)
Mivel az eredeti változat rpm csomagba volt, így várható, hogy nem fog tökéletesen működni. Nem kell megijedni, ezt csak az adatbázis frissítésére vonatkozik! Hiába próbáljuk meg rendszergazdaként online frissíteni, mindig hibára fog futni a frissítés. Valószínűleg trükközéssel lehet frissíteni, de még nem jöttem rá a megfelelő megoldásra. Ettől a program használható, mivel túl régi nem lehet az adatbázis.

(Kiegészítés: Kipróbáltam újra a frissítést és még mindig hibára fut, ennek ellenére a log napló bejegyzése szerint sikeresen települt. Valószínűleg frissítés után olyan műveletet szeretne végezni, mely hibára fut és emiatt jelenik meg megtévesztő hibaüzenet.)

3. F-prot

Ezt a programot azért hagytam utolsónak, mert nem volt idő kipróbálni. Az <a href=http://www.f-prot.com/download/home_user/download_fplinux.html>F-prot</a> oldaláról letölthető a deb csomag, mely könnyedén telepíthető:
sudo dpkg -i fp-linux-ws.deb
Telepítés után konzolon keresztül használható a program, de jobb lenne grafikus felületen használni. Erre készült egy GTK-s felület, melyet még nem telepítettem, de leírás olvasható a <a href=http://doc.gwos.org/index.php/F-prot_gtk>http://doc.gwos.org/index.php/F-prot_gtk</a> web oldalon.
Sok sikert a telepítéshez.
