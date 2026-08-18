---
author: kecsi
categories:
- x
created: 1107349005
date: '2005-02-02T00:00:00Z'
excerpt: 'Legszerűbben elindítod egy shellben <strong>xwininfo</strong> nevű progit majd ráböksz az ablakra aminek az infóira kíváncsi vagy.\r\n\r\nDe ha pl. én a <a href="http://www.goof.com/pcg/marc/root-tail.html">root-tail</a> log kiiró X-es alkalmazással a desktopom(Xfce) root ablakába akarok kiratni egy megadott log allományt, minden X induláskor automatikusan, akkor létrehozok egy ~/Desktop/Autostart/roottail shellszkriptet a következő tartalommal:\r\n<strong>#!/bin/bash\r'
title: Xwindow ablak informació
aliases:
- /node/14/
- /story/14/
---
Legszerűbben elindítod egy shellben <strong>xwininfo</strong> nevű progit majd ráböksz az ablakra aminek az infóira kíváncsi vagy.

De ha pl. én a <a href="http://www.goof.com/pcg/marc/root-tail.html">root-tail</a> log kiiró X-es alkalmazással a desktopom(Xfce) root ablakába akarok kiratni egy megadott log allományt, minden X induláskor automatikusan, akkor létrehozok egy ~/Desktop/Autostart/roottail shellszkriptet a következő tartalommal:
<strong>#!/bin/bash
root-tail -f -id `xwininfo -name "Desktop" | grep "Window id"| cut -d" " -f4` -g 1250x930+20+10 -fn -ttf-tahoma-bold-*-normal-*-12-*-*-*-*-*-*-* /var/log/syslog,darkgreen</strong>
Amiben ugye az -id XWINDOW_ID paramatert a xwininfo segítségével nyerem ki. A font megadsáházoz javallom az xfontsel progi tanulmányozását. Végül nem felejtek el futatási jogot adni a létrehozott állományra. :)
