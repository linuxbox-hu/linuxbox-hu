---
excerpt: "Az alap (vanilla) kernel sajátossága, hogy minden felhasználó láthatja mások
  processzeit.\r\nErre a problémára léteznek ugyan különböző megoldások (pl. grsecurity),
  de ezek mind \"macerásak\".\r\nMilyen jó is volna, ha különösebb varázslat nélkül
  el lehetne érni, hogy mindenki csak a saját folyamatait lássa pl. a <code>ps axu</code>
  parancsnál.\r\n\r"
categories:
- linux
layout: story
author: Goosfrabaa
mail: gabrea@freemail.hu
title: Processzek elrejtése
created: 1330640227
---
Az alap (vanilla) kernel sajátossága, hogy minden felhasználó láthatja mások processzeit.
Erre a problémára léteznek ugyan különböző megoldások (pl. grsecurity), de ezek mind "macerásak".
Milyen jó is volna, ha különösebb varázslat nélkül el lehetne érni, hogy mindenki csak a saját folyamatait lássa pl. a <code>ps axu</code> parancsnál.

Úgy néz ki, hogy végre Linus is belátta az igény jogossságát és a 3.3-as kernelben megjelenik a hőn áhított funkció.
Lényegében a <code>/proc</code> filerendszert kell a <code>"hidepid=1"</code> opcióval mountolni és kész is.
A hírt <a href="http://www.nux.ro/archive/2012/02/Hide_other_users__processes_in_Linux.html">itt találtam</a>.
