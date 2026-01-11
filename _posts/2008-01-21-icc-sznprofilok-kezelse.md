---
excerpt: "Monitor (szkenner, nyomtató, fényképező gép) kalibrálása után kedvenc operációs
  rendszerünkkel is meg kell ismertetni az ICC színprofil állományt.\r\nUtánanéztem,
  hogy is megy ez Linux alatt:\r\n<a href=\"http://jcornuz.wordpress.com/2007/09/26/color-managed-monitor-i/\">Ezen</a>
  a címen angolul olvasható egy rövid leírás, mely két parancssori megoldást kínál:\r\n<ul>\r\n<li>Az
  <a href=\"http://www.etg.e-technik.uni-erlangen.de/web/doe/xcalib/\">xcalib</a>
  (az opcionálisan megadható kapcsolók után) mindössze az ICC fájl nevét várja\r\n</li>\r"
categories:
- x
layout: story
author: Goosfrabaa
title: ICC színprofilok kezelése
created: 1200957213
---
Monitor (szkenner, nyomtató, fényképező gép) kalibrálása után kedvenc operációs rendszerünkkel is meg kell ismertetni az ICC színprofil állományt.
Utánanéztem, hogy is megy ez Linux alatt:
<a href="http://jcornuz.wordpress.com/2007/09/26/color-managed-monitor-i/">Ezen</a> a címen angolul olvasható egy rövid leírás, mely két parancssori megoldást kínál:
<ul>
<li>Az <a href="http://www.etg.e-technik.uni-erlangen.de/web/doe/xcalib/">xcalib</a> (az opcionálisan megadható kapcsolók után) mindössze az ICC fájl nevét várja
</li>
<li>a <strong>dispwin</strong> egy sokkal komplexebb megoldást nyújtó program az <a href="http://argyllcms.com/">ArgyllCMS </a> csomag része
 </li>
</ul>Mindkét programnak létezik MS verziója is!

A fentieken kívül szóba jöhet még az <a href="http://www.burtonini.com/blog/computers/xicc">xicc</a> parancs is.
Aki pedig a grafikus beállító programokat részesíti előnyben, az használja az <a href="http://lprof.sourceforge.net/">lproof</a>-ot!

