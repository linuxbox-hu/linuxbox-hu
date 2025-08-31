---
excerpt: "\"Screen egy teljes képernyős ablakkezelő, ami megtöbbszörözi a fizikai
  terminálod processzek és természetesen shell programok segítségével: így több virtuális
  terminált szolgáltat egy shellen...\"\r\n\r\nNem szándékozom teljes leírást készíteni,
  de fel szeretném kelteni azok figyelmét akik még nem ismerik és meg szeretném mutatni
  azoknak akik már használják a programot, hogy én mely szolgáltatásait használom.\r\n"
categories:
- linux
layout: story
author: kecsi
mail: kecsi@linuxbox.hu
title: '"Ablak kezelés" konzolon; screen'
created: 1122917599
---
"Screen egy teljes képernyős ablakkezelő, ami megtöbbszörözi a fizikai terminálod processzek és természetesen shell programok segítségével: így több virtuális terminált szolgáltat egy shellen..."

Nem szándékozom teljes leírást készíteni, de fel szeretném kelteni azok figyelmét akik még nem ismerik és meg szeretném mutatni azoknak akik már használják a programot, hogy én mely szolgáltatásait használom.
<!--break-->
<ul>Kezdjük mindjárt az elején:
<li><strong>screen</strong>
o [shellből] egy új környezet létrehozása</li>
<li><strong>screen -R</strong>
o [shellből] csatlakozás egy korábban félbehagyott munkához</li>
<li><strong>screen -DD -R</strong>
o [shellből] csatlakozás egy korábban kilépés nélkül félbehagyott munkafolyamathoz</li>
<li><em>Ctrl-a + c</em>
o [billentyűkombináció működés közben] egy új virtuális ablak létrehozása</li>
<li><em>Ctrl-a + k</em>
o [bill.] virtuális ablak bezárása</li>
<li><em>Ctrl-a Ctrl-a</em>  vagy <em>Ctrl-a Szóköz</em>
o [bill.] következő ablakra váltás</li>
<li><em>Ctrl-a + S</em>
o [bill.] jelenlegi ablak kettéosztása</li>
<li><em>Ctrl-a + TAB</em>
o [bill.] mozgás a szétosztott ablakok közt</li>
<li><em>Ctrl-a + A</em>
o jelenlegi ablak elnevezése</li>
<li><em>Ctrl-a + "</em>
o [bill.] összes ablak listája - mozgás az ablakok közt a nyilakkal</li>
<li><em>Ctrl-a + d</em>
o [bill.] és vegül a leglényegesebb. ezzel deattach-olni azaz magára lehet hagyni amit legközelebb újra lehet folytatni</li>
</ul>
