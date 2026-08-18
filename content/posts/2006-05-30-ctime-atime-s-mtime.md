---
author: kecsi
categories:
- linux
created: 1148981416
date: '2006-05-30T00:00:00Z'
excerpt: Fontos különbséget tenni állományok és könyvtárak hozzáférési jogok változási ideje (change time - ctime), utolsó hozzáférés ideje (access time - atime) és utolsó módosítás ideje (modify time - mtime) közt. ctime - UNIX-ban, nem tudjuk megmondani, mikor keszült el egy állomány. A "ctime - change time" az utolsó hozzáfárási szabályok módosítását adja meg állományokon és könyvtárakon egyaránt (tulaj [owner], jogosultság [permissions]). Ezt az információt használja például a dump parancs is mikor meghatározza hogy az állományt kell elmentenie. A ctime lekérdezése listázáskor az ls -lc paranccsal végezhetjük.
title: ctime, atime és mtime
aliases:
- /node/171/
- /story/171/
---
Fontos különbséget tenni állományok és könyvtárak hozzáférési jogok változási ideje (change time - ctime), utolsó hozzáférés ideje (access time - atime) és utolsó módosítás ideje (modify time - mtime) közt.

ctime - UNIX-ban, nem tudjuk megmondani, mikor keszült el egy állomány. A "ctime - change time" az utolsó hozzáfárási szabályok módosítását adja meg állományokon és könyvtárakon egyaránt (tulaj [owner], jogosultság [permissions]). Ezt az információt használja például a dump parancs is mikor meghatározza hogy az állományt kell elmentenie. A ctime lekérdezése listázáskor az <code>ls -lc</code> paranccsal végezhetjük.

atime - az az időpont amikor az adatot utoljára olvastuk. pl. kiirattuk a tartalmát, futtattuk stb. atime lekérdezése listázáskor: <code>ls -lu</code>

mtime - az állomány tartalmának utolsó módosítását adja Ez a időpont szerepel a hosszú listában <code>ls -l</code>.

Linuxon a <code>stat</code> parancs mindhárom adatot megmutatja.
