---
excerpt: "Ha egy hosszadalmas, gépigényes folyamatot futtatunk, de nem szeretnénk,
  ha a többi user ebből bármit is megérezne, akkor vessük be az ionice és nice programokat.\r\n"
categories:
- linux
layout: story
author: andrewjsi
title: Program futtatása csak üresjáratban
created: 1340771023
---
Ha egy hosszadalmas, gépigényes folyamatot futtatunk, de nem szeretnénk, ha a többi user ebből bármit is megérezne, akkor vessük be az ionice és nice programokat.
<!--break-->
Például kernelforgatás 5 szálon úgy, hogy csak akkor haladjon a munka, ha amúgy a processzor és a lemez nem csinálna semmit:

<code>ionice -c 3 nice -n 20 make -j5</code>
