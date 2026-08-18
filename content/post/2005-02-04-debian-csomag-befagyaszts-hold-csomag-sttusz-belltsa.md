---
author: kecsi
categories:
- debian
created: 1107511687
date: '2005-02-04T00:00:00Z'
description: 'Lekérdezzük a csomagok jelenlegi statuszát: dpkg --get-selections \* > selections.txt Majd szerkesszük a készített állományt. Megkeresed a csomagod: pine install Átírod a statuszát: pine hold Majd érvényesíted a változtatásokat: dpkg --set-selections < selections.txt'
title: debian csomag befagyasztás; "hold" csomag státusz beállítása
aliases:
- /node/18/
- /story/18/
---
Lekérdezzük a csomagok jelenlegi statuszát:
`dpkg --get-selections \* &gt; selections.txt`

Majd szerkesszük a készített állományt.
Megkeresed a csomagod:
     pine                                           install
Átírod a statuszát:
     pine                                           hold
Majd érvényesíted a változtatásokat:
`dpkg --set-selections &lt; selections.txt`
