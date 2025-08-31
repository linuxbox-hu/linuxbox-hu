---
excerpt: "Egyik Ubuntu 9.04-et használó barátom kérdezett meg arról, hogy hogyan tudná
  megoldani a laptopján, hogy otthon 1-képernyős XOrg beállításokkal, míg munkahelyén
  két képernyős XOrg beállításokkal indíthassa kedvenc operációs rendszerét, mindemellett
  ne kelljen a váltáshoz újraindítani az XOrg-ot.\r\n\r\nEgy kis töprengés után a
  következő tippet adtam neki:\r\n\r"
categories: []
layout: blog
author: tibcsi
mail: tibalogh@gmail.com
title: Váltás egyképernyős és dual-képernyős üzemmód között Grub menü segítségével
created: 1255352395
---
Egyik Ubuntu 9.04-et használó barátom kérdezett meg arról, hogy hogyan tudná megoldani a laptopján, hogy otthon 1-képernyős XOrg beállításokkal, míg munkahelyén két képernyős XOrg beállításokkal indíthassa kedvenc operációs rendszerét, mindemellett ne kelljen a váltáshoz újraindítani az XOrg-ot.

Egy kis töprengés után a következő tippet adtam neki:

A Grub menüben vegyen fel egy új menüpontot ugyanazzal a kernellel, mint amit használ, és egészítse ki a kernel opciókat egy 'dualkepernyo' szócskával. Valahogy így:

<code>
title       Ubuntu 9.04, Egykepernyos
kernel      /vmlinuz-2.6.28-15-generic root=... ro quiet splash
initrd      /initrd.img-2.6.28-15-generic
quiet

title       Ubuntu 9.04, Ketkepernyos
kernel      /vmlinuz-2.6.28-15-generic root=... ro quiet splash dualkepernyo
initrd      /initrd.img-2.6.28-15-generic
quiet
</code>

Tehát két menüpont legyen, az egyik az egyképernyős, a másik pedig a kétképernyős üzemmód.
Ezután hozzon létre egy init scriptet az /etc/init.d -ben dualkepernyo néven, ami a következőt tartalmazza:

<code>
#!/bin/sh
if grep -q -w -- "-s\|dualkepernyo\|S" /proc/cmdline; then
&nbsp;&nbsp;cp /etc/X11/xorg.dual.conf /etc/X11/xorg.conf
else
&nbsp;&nbsp;cp /etc/X11/xorg.single.conf /etc/X11/xorg.conf
fi 
</code>

Ez a script nem csinál mást, minthogy ellenőrzi, szerepel-e a kernel-opciók között a 'dualkepernyo' szócska.
Ettől függően a választott boot-menünek megfelelő XOrg konfigurációs fájlt másolja a helyére. 
<em>Természetesen ezeket a konfigurációs fájlokat előzetesen létre kell hozni a megfelelő XOrg beállításokkal.</em>

Már csak azt kell elérni, hogy a script lefusson boot-időben, még a gdm indulása előtt:

<code>
chmod 755 /etc/init.d/dualkepernyo
ln -s /etc/init.d/dualkepernyo /etc/rc2.d/S29dualkepernyo
</code>

A 2-es futási szintbe tettem, mivel Ubuntu 9.04-ben ez az alapértelmezett futási szint. A sorrend meghatározásához pedig 1-gyel kisebb számot (S29-et) használtam, mint a gdm sorrendje - mivel nálam a gdm S30-as.

Elég csúnya megoldásnak tűnik, de működött :)


