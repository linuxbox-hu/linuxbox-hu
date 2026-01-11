---
excerpt: "Lekérdezzük a csomagok jelenlegi statuszát:\r\n<strong>dpkg --get-selections
  \\* &gt; selections.txt</strong>\r\n\r\nMajd szerkesszük a készített állományt.\r\nMegkeresed
  a csomagod:\r\n     pine                                           install\r\nÁtírod
  a statuszát:\r\n     pine                                           hold\r\nMajd
  érvényesíted a változtatásokat:\r\n<strong>dpkg --set-selections &lt; selections.txt</strong>"
categories:
- debian
layout: story
author: kecsi
title: debian csomag befagyasztás; "hold" csomag státusz beállítása
created: 1107511687
---
Lekérdezzük a csomagok jelenlegi statuszát:
<strong>dpkg --get-selections \* &gt; selections.txt</strong>

Majd szerkesszük a készített állományt.
Megkeresed a csomagod:
     pine                                           install
Átírod a statuszát:
     pine                                           hold
Majd érvényesíted a változtatásokat:
<strong>dpkg --set-selections &lt; selections.txt</strong>
