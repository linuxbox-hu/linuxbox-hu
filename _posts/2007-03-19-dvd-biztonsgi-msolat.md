---
excerpt: "Biztos másokkal is megtörtént, hogy kedvenc DVD lemeze lejátszása közben
  megakadt a lejátszás, esetleg teljesen leállt. Én egy újsághoz adott DVD filmmel
  jártam így és mivel meg szerettem volna tartani elkezdtem utána járni, hogyan menthető
  meg.\r\nFigyelmeztetés: Csak biztonsági másolat készítésére szabad használni az
  itt felsorolásra kerülő programokat!!!\r\n\r"
categories: []
layout: blog
author: sanya
mail: snagy.sandor@gmail.com
title: DVD biztonsági másolat
created: 1174301987
---
Biztos másokkal is megtörtént, hogy kedvenc DVD lemeze lejátszása közben megakadt a lejátszás, esetleg teljesen leállt. Én egy újsághoz adott DVD filmmel jártam így és mivel meg szerettem volna tartani elkezdtem utána járni, hogyan menthető meg.
Figyelmeztetés: Csak biztonsági másolat készítésére szabad használni az itt felsorolásra kerülő programokat!!!

Anno még Windows-on oldottam meg a mentést, de mára áttértem Linux-ra és sajnos át kellet hoznom néhány programot, mivel kevés Linux-os megoldást találtam. Windows-on elegendő a DVDShrink használata, mellyel minden folyamat megoldható. (Program weblapja: <a href=http://www.dvdshrink.org>www.dvdshrink.org</a>, letölteni innen nem lehet, érdemes a <a href=http://www.google.hu>www.google.hu</a> oldalon megkeresni.) Mivel a DVDShrink Linux-os verziójával nem boldogultam és nem is nyújtotta a Windows-os változat szolgáltatásait, így maradtam a Wine alatt futtatható Windows-os verziónál. Ennek sajnos az a hátránya, hogy nem tudja a filmet közvetlenül a lemezről átkódolni és másik lemezre írni. Viszont az átkódolás folyamata jól működik. (Gyors munkát és jó minőséget kapunk.) Mivel a lemez védet, így első lépésben át kell másolni az adatokat a merevlemezre a védelem feltörésével. Erre készítették a vobcopy nevű parancssoros programot, mely az alap Ubuntu tárolók közt megtalálható. Használata egyszerű, csak ki kell adni a vobcopy –m parancsot. Ez nem más, mint a mirror funkció, mely egy az egybe átmásolja a lemez tartalmát. Ezek után már a DVDShrink gond nélkül át tudja kódolni a filmet írható lemez méretűre. (Ha ezt nem szeretnénk, akkor egy dupla rétegű lemezre is ki lehet írni a filmet.) Mivel már a merevlemezen van a film, így az open files ikonnal meg kell nyitnunk a VIDEO_TS könyvtárat. Ekkor elemzi annak tartalmát és megjelennek a filmmel kapcsolatos információk. Érdemes kiszedni a felesleges hangsávokat illetve eltávolítani a felesleges extrákat a menüből, így jobb képminőség érhető el, mivel kevesebb adat kerül a lemezre. Rengeteg szolgáltatást nyújt, melyet érdemes kihasználni és csak utána ráklikkelni a backup ikonra. Miután végzett az adatok feldolgozásával könnyedén kiírható a jól megszokott K3B-vel.
(További ötleteket nem írok, mivel ezzel illegális másolatok készíthetők és nem szeretném a weboldal készítőjét kellemetlen helyzetbe hozni!)
