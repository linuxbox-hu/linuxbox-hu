---
excerpt: "A napokban úgy adódott, hogy hálózati ábrát kellett készítenem. A dia nevű
  programot szerettem volna használni, mivel alapjában véve nem dolgozom windowson.
  Azonban a programhoz nem voltak megfelelő ábrák. Nem maga a kép hiányzott, hanem
  vele együtt a csatlakozási pontok is. Utána jártam miként lehet a célnak megfelelő
  alakokat készíteni megfelelő számú csomóponttal.\r\n"
categories: []
layout: blog
author: siposg
title: Dia bővítmény elkészítése
created: 1306091115
---
A napokban úgy adódott, hogy hálózati ábrát kellett készítenem. A dia nevű programot szerettem volna használni, mivel alapjában véve nem dolgozom windowson. Azonban a programhoz nem voltak megfelelő ábrák. Nem maga a kép hiányzott, hanem vele együtt a csatlakozási pontok is. Utána jártam miként lehet a célnak megfelelő alakokat készíteni megfelelő számú csomóponttal.
<!--break-->
<strong>- Először is meg kell rajzolni amit szeretnénk képként látni. Mondjuk legyen egy rackbe szerelhető switch. </strong>
Ennek megrajzolása jónéhány téglalap alakú dobozka összessége. Először is rajzoljuk meg azt a téglalapot mely magát az eszközt reprezentálja. Aztán nagyítsuk jó nagyra és rajzoljunk bele picike négyzeteket, melyek az egyes RJ-45 csatlakozóknak megfelelők. Tegyük háttérbe a nagy téglalapot és adjunk neki pl szürke háttérszínt. Ezzel nagyjából készen vagyunk az első alakkal, melyet egy alak készletbe betölthetünk.

<strong>- Bővítsül fel az egyik alakkészletet az új ábrával.</strong>
Mentsük el az ábrát a szokásos módon. Ezután exportáljuk shape formátumban a <code>~/.dia/shapes/</code> könyvtárba. A kérdésekre adjunk alapértelmezett válaszokat. Nyissuk meg a Fájl - Munkalapok és objektumok menüpontot, majd válasszuk ki a bal oldali listából a "Hálózat" nevű alakkészletet. Nyomjuk meg alul az Új gombot és válasszuk ki az svn alak rádiógombot. Írjuk be a shapes fájl teljes elérési útját (betallózni nem tudjuk a rejtett könyvtárakat) <code>~/.dia/shapes/switch.shape</code> a fájlnév mezőbe. Írjuk be az értelmes emberi nevet a leírás mezőbe. Ez utóbbi fog felbukkanó súgóként a kép felett megjelenni. Nyomjuk meg a hozzáadás gombot. Ekkor a Hálózat készletben megjelenik az új alakzat. Ne felejtsünk el az alkalmaz gombra rákattintani, mielőtt zárjuk az ablakot.

<strong>-Ellenőrzés, finomítás:</strong>
Ezt követően láthatjuk az új alakzatot a Hálózat készletben! Próbáljuk ki hogyan tudjuk egy dia ábrán elhelyezni és milyen csomópontokhoz lehet kapcsolatokat megadni. A csomópontokkal még egy kicsit játszani kell valószínűleg. Minden olyan pont ami az eredeti rajzba beillesztett téglalap valamely csomópontja volt, az új ábrán is csomópontként jelentkezik. Ez nem feltétlenül szerencsés. A módosításhoz célszerű a shape fájlt szerkeszteni. Minden point kezdetű sor egy elérhető csomópontot jelent. Ezeket kell megtizedelni. Minden RJ-45 csatlakozónak egy csomópontja legyen, magának a switchnek meg egyáltalán nem kell külön.

<strong>- Készítsünk saját új alakzat készletet:</strong>
Ennek mi értelme? Az, hogy hordozhatóvá tudjuk tenni a készletünket, illetve meg tudjuk osztani kollégáinkkal.
Készítsük el tehát az új készletet: Fájl - Munkalapok és objektumok - Új - Munkalap neve rádiógomb. Munkalap neve: "Proba" Leírás: "Próba készlet", majd "Ok" gomb. Elkészült az új készlet, ezzel a <code>~/.dia/sheets/</code>könyvtárba bekerült egy új fájl <code>proba.sheet</code> néven.
A készletet fel lehet tölteni a fentiekben leírt módon, illetve úgy gondolom magáért beszél. A dia programot újraindítva az új készlet is a készletek között látható, az általunk elhelyezett alakzatokkal.

- </strong>Lássunk egy példát, használható ikonkészletekkel, egyéb leírással:</strong> http://dia-installer.de/shapes.html

<strong>- Milyen fájlok szükségesek egy teljes ikonkészlethez?</strong>
~/.dia/sheets/ikonkeszlet.sheet
~/.dia/shapes/ikonom.shape
~/.dia/shapes/ikonom.png

<strong>- Fontosabb tudnivalók a szöveges fájlokról:</strong>
Sheet fájl egy bejegyzése:
<code> <strong>&lt;name&gt;Racks&lt;/name&gt; </strong> #A készlet neve
  <strong>&lt;name xml:lang="cs_CZ"&gt;Racky&lt;/name&gt;</strong></code> # A készlet Cseh neve

<code><strong> &lt;object name="Racks - Rack 16U"&gt; </strong># alakzat neve
      <strong>&lt;description&gt;Half-Rack 16U&lt;/description&gt; </strong># Angol nyelvű leírás
      <strong>&lt;description xml:lang="cs_CZ"&gt;Pulrack 16U&lt;/description &gt; </strong># Cseh nyelvű leírás
    <strong>&lt;/object&lt; </strong><code>

Remélem kedvet csináltam a program használatához, bővítéséhez!
Kellő mennyiségű ábra elkészítése, vagy internetről letöltése, telepítése (bemásolása a ~/.dia/ könyvtárba) után a visio helyettesítőjeként nagyszerűen használható hálózati ábra készítő program a dia.

<a href="http://linuxscripting.hu">linuxscripting</a>
