---
excerpt: "Azaz, hogyan lehet egyből exponálás után számítógépen megjeleníteni a képeket?\r\n"
categories:
- linux
layout: story
author: Goosfrabaa
mail: gabrea@freemail.hu
title: Nikon tethered shooting
created: 1319098603
---
Azaz, hogyan lehet egyből exponálás után számítógépen megjeleníteni a képeket?
<!--break-->
A <a href="http://www.nikoncafe.com/vforums/showthread.php?p=2105147">nikoncafen</a> azt írják, hogy a <strong>gphoto2</strong>-vel és egy képnézővel (a példában <strong>gwenviewt</strong> használtak de lényegében bármi jó) viszonylag egyszerűen "valós időben" nézhetjük meg képeinket számítógépen, amennyiben USB kábellel összekapcsoltuk az eszközöket.

A parancs:
<code>gphoto2 --capture-tethered --hook-script tethered.sh</code>

Itt pedig a <a href="http://pastebin.com/6nbAc0db">tethered.sh</a> szkript.
A szkript a nyers (raw) fájlokat nem próbálja meg betölteni, de pl. a <a href="http://rawstudio.org/">rawstudio</a>val ez is lehetséges.

Ha másik fényképezőgépet szeretnénk használni, a <code>gphoto2 --config</code> paranccsal konfigolhatjuk újra a rendszert.
Amennyiben számítógépről szeretnénk az expozíciót indítani, olvasgassuk <a href="http://gphoto.org/doc/remote/">ezt</a>.
 

Egy másik, frissebb <a href="http://rian76.blogspot.com/2009/09/tethering-from-your-nikon-to-your-linux.html">leírás</a> szerint a (<strong>gphoto2</strong> fejlődése miatt) elég ezt a <a href="http://pastebin.com/k9TYHGhe">tether</a> szkriptet lefuttani egy üres könyvtárban állva. Ennél a szkriptnél a <strong>qiv</strong> képnézőt használták
