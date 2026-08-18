---
author: kecsi
categories:
- linux
created: 1122917599
date: '2005-08-01T00:00:00Z'
excerpt: '"Screen egy teljes képernyős ablakkezelő, ami megtöbbszörözi a fizikai terminálod processzek és természetesen shell programok segítségével: így több virtuális terminált szolgáltat egy shellen..."\r\n\r\nNem szándékozom teljes leírást készíteni, de fel szeretném kelteni azok figyelmét akik még nem ismerik és meg szeretném mutatni azoknak akik már használják a programot, hogy én mely szolgáltatásait használom.\r\n'
title: '"Ablak kezelés" konzolon; screen'
aliases:
- /node/88/
- /story/88/
---
"Screen egy teljes képernyős ablakkezelő, ami megtöbbszörözi a fizikai terminálod processzek és természetesen shell programok segítségével: így több virtuális terminált szolgáltat egy shellen..."

Nem szándékozom teljes leírást készíteni, de fel szeretném kelteni azok figyelmét akik még nem ismerik és meg szeretném mutatni azoknak akik már használják a programot, hogy én mely szolgáltatásait használom.
<!--break-->
<ul>Kezdjük mindjárt az elején:
<li>`screen`
o [shellből] egy új környezet létrehozása</li>
<li>`screen -R`
o [shellből] csatlakozás egy korábban félbehagyott munkához</li>
<li>`screen -DD -R`
o [shellből] csatlakozás egy korábban kilépés nélkül félbehagyott munkafolyamathoz</li>
<li>`Ctrl-a + c`
o [billentyűkombináció működés közben] egy új virtuális ablak létrehozása</li>
<li>`Ctrl-a + k`
o [bill.] virtuális ablak bezárása</li>
<li>`Ctrl-a Ctrl-a`  vagy `Ctrl-a Szóköz`
o [bill.] következő ablakra váltás</li>
<li>`Ctrl-a + S`
o [bill.] jelenlegi ablak kettéosztása</li>
<li>`Ctrl-a + TAB`
o [bill.] mozgás a szétosztott ablakok közt</li>
<li>`Ctrl-a + A`
o jelenlegi ablak elnevezése</li>
<li>`Ctrl-a + "`
o [bill.] összes ablak listája - mozgás az ablakok közt a nyilakkal</li>
<li>`Ctrl-a + d`
o [bill.] és vegül a leglényegesebb. ezzel deattach-olni azaz magára lehet hagyni amit legközelebb újra lehet folytatni</li>
</ul>
