---
author: andrewjsi
categories:
- linux
created: 1340771023
date: '2012-06-27T00:00:00Z'
description: |
  Ha egy hosszadalmas, gépigényes folyamatot futtatunk, de nem szeretnénk, ha a többi user ebből bármit is megérezne, akkor vessük be az ionice és nice programokat.
title: Program futtatása csak üresjáratban
aliases:
- /node/711/
- /story/711/
---
Ha egy hosszadalmas, gépigényes folyamatot futtatunk, de nem szeretnénk, ha a többi user ebből bármit is megérezne, akkor vessük be az ionice és nice programokat.
<!--break-->
Például kernelforgatás 5 szálon úgy, hogy csak akkor haladjon a munka, ha amúgy a processzor és a lemez nem csinálna semmit:

<code>ionice -c 3 nice -n 20 make -j5</code>
