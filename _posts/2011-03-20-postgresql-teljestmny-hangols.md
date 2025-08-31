---
excerpt: "A nyílt forrású adatbázis motorok közül leghíresebb és talán legelterjedtebb
  a Mysql. A MysqlAB fejlesztette eredetileg. A Mysqlab fejlesztőcéget felvásárolta
  a Sun, majd Őket az Oracle. A felvásárlás után az Oracle lépései között több olyan
  is található, mely a nyílt forrású közösség ellenérzését vívta ki. Bár a mysql eddig
  nem szenvedett el ilyen problémás lépést, mégis felmerül a kérdés mi van, ha mégis?\r\n"
categories:
- ubuntu
layout: story
author: siposg
mail: rg@linuxscripting.hu
title: Postgresql teljesítmény hangolás
created: 1300635058
---
A nyílt forrású adatbázis motorok közül leghíresebb és talán legelterjedtebb a Mysql. A MysqlAB fejlesztette eredetileg. A Mysqlab fejlesztőcéget felvásárolta a Sun, majd Őket az Oracle. A felvásárlás után az Oracle lépései között több olyan is található, mely a nyílt forrású közösség ellenérzését vívta ki. Bár a mysql eddig nem szenvedett el ilyen problémás lépést, mégis felmerül a kérdés mi van, ha mégis?
<!--break-->
Egy véleményem szerint méltatlanul háttérbe szorult, nagyon jó alternatíva a Postgresql szerver. Régóta használom, ahol lehet mysql helyett telepítem. Sok olyan vád érte, hogy lassú. Aztán készültek mérések melyek szerint fej-fej mellett versenyeznek a mysql-lel.
Nem árt tudni, hogy a postgresql nagyon drasztikus mértékben hangolható a futtató gép képességeitől függően. Lássunk pár példát, mit és milyen módon lehet hangolni. A postgresql.conf fájlban található paraméterek közül fogok párat bemutatni.

<code>shared_buffer</code> 
Alap helyzetben 24-32 MB-ra van beállítva. Ez a legtöbb rendszeren a biztonságosan használható érték. Azonban igen kevés, ráadásul linuxon keményen megemelhető. 
Tipikusan a fizikai RAM 15%-a adható meg. Amennyiben a gépben 1 GB RAM vagy annál kevesebb található, akkor nem célszerű feljebb emelni. 
2GB RAM mellett azonban érdemes többet adni pl a ram 25%-át. Ez testvérek között is 512MB.

<code>work_mem</code>
A sorba rendezések (ORDER BY) az így megadott memória mennyiséget használják. Bonyolultabb lekérdezések esetén, ahol több mező szerint is rendezünk, kevés lehet az alapértelmezett érték, mely 1MB. Ha ez a mennyiség nem elég, akkor a rendezéshez szükséges adatokat azonnal a merevlemezre írja, melytől a rendezés sebessége a tizedére esik vissza.
50 MB általában egészen jó érték. Magasabb értéket, csak mérés után érdemes beállítani, és figyelni kell közben a fizikai RAM illetve az abból elhasznált mennyiséget. Nagyon oda kell figyelni hány connection lehetséges, mert minden csatlakozott user képes futtatni olyan processzt, mely elhasznál egy-egy adag work_mem-et. Számolni kell a userek száma * joinek száma a lekérdezésben * work_mem értékét. Lehetőleg ne fogyjunk ki a Fizikai memóriából, mert akkor indul a swap használat, ezért ugyan ott vagyunk, ahonnan elindultunk.
256MB egészen extrém érték és igen sok fizikai RAM és alacsony max_connections érték mellett célszerű alkalmazni.

<code>effective_cache_size</code>
A fizikai RAM 50%-a egy egészen jó érték. A fizikai RAM 75%-a egészen extrém érték!

Ellenőrzések
Először is futtassuk le a korábban lassúnak talált lekérdezéseket és mérjük meg a futási időt.
Ellenőrizzük, hogy érvényre jutottak-e valóban a beállításaink: psql> SHOW ALL;
Mérjünk teljesítményt a pg_bench alkalmazással, melyet pl. ubuntura az <code>apt-get install postgresql-contrib-8.x</code> paranccsal telepíthetünk rootként.

Megjegyzések:
- A fenti pár beállítás elsősorban a lekérdezések gyorsítására alkalmas módosítás. Olyankor hasznos, amikor az alkalmazást nem lehetséges módosítani.
- A fizikai RAM mennyiségére mindvégig oda kell figyelni, különösen akkor, ha más alkalmazások is futnak a rendszeren. Ha elfogyasztjuk az összes memóriát, először swappelés indul be, később kritikus állapot is előállhat. Számolással, tesztekkel előzzük meg!
- A leírás messze nem teljeskörű, csupán betekintést enged a postgres teljesítményhangolásba.
- Mielőtt a postgres hangolásába kezdünk, mérjük ki a lassúnak talált alkalmazás által futtatott lekérdezéseket. Ha a lassú műveletek hosszát nem a postgresben futó lekérdezések okozzák, nem érdemes hangolni.

<a href="http://linuxscripting.hu/suli">linuxscripting.hu</a>
