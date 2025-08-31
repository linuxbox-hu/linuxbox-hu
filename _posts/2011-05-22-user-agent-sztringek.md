---
excerpt: A curl és a wget grabber programok. Megadható, hogy mely böngészőnek adják
  ki magukat letöltés közben. Egyrész nem szép dolog megváltoztatni a beépített user
  agent sztringet, másrészt az élet kényszerít rá. Gondoljunk csak az Opera böngésző
  régebbi változataira, amelyekben meg lehetett adni, hogy Internet explorernek álcázza
  magát. Miért?
categories: []
layout: blog
author: siposg
mail: rg@linuxscripting.hu
title: User agent sztringek
created: 1306052095
---
A curl és a wget grabber programok. Megadható, hogy mely böngészőnek adják ki magukat letöltés közben. Egyrész nem szép dolog megváltoztatni a beépített user agent sztringet, másrészt az élet kényszerít rá. Gondoljunk csak az Opera böngésző régebbi változataira, amelyekben meg lehetett adni, hogy Internet explorernek álcázza magát. Miért? Mert ilyenkor az oldalak letöltődtek és olvashatók voltak, míg normál beállítás mellett egy üzenet fogadta a felhasználót, pl nem támogatott böngésző.

A wget esetén ez a megfelelő kapcsoló: <code>--user-agent="Mozilla..."</code>
A curl esetén: <code>--user-agent</code> vagy a <code>--header</code>

Mivel a webszerverek naplófájljaiban az eredeti helyett ezek a sztringek jelennek meg, illetve a statisztikák emiatt módosulnak, csak szükség esetén használjuk ezeket a kapcsolókat.

<a href="http://linuxscripting.hu/suli">Linuxscripting</a>
