---
author: Goosfrabaa
categories:
- linux
created: 1245069457
date: '2009-06-15T00:00:00Z'
title: Hogy mi használja eszeveszettül a merevlemezt
---
megmondja az <a href="http://www.atcomputing.nl/Tools/atop/">atop</a> ami a legtöbb disztribúcióban csomagként elérhető.

A parancssoros (ám színes megjelenítésre képes) programot legalábbis erre használom főleg.
Persze ezen kívül tud mindent, ami egy rendszer monitorozó programtól elvárható:
processzor, lemez, memória, hálózat, swap átvitel/terheltség vizsgálatot periódikusan mérve, mint a <strong>top</strong>.

Számtalan kapcsolóval lehet indítani, amelyek funkcióját interaktívan is előcsalhatjuk a megfelelő billentyűk lenyomásával.
Pl a címben említett vizsgálatot az <strong>atop -dD</strong> kapcsolókkal szoktam végezni.
