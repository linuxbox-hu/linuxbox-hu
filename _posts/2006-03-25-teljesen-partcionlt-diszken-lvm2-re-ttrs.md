---
excerpt: "<em>Avagy hogyan lehet egy resize-t eltolni, aztán helyrehozni :)</em>\r\n\r\n\r\n<strong>Kiindulás</strong>\r\n\r\nAdott
  egy 80Gb-os winchester:\r\n<ol>\r\n<li>8Gb NTFS a WinXP-nek (hátha kell),</li>\r\n<li>200Mb
  ext3 /boot</li>\r\n<li>1Gb swap</li>\r\n<li>8Gb reiser3 /</li>\r\n<li>maradék ext2
  /mnt/D (windows alól D ext2-höz való IFSD-vel)</li>\r\n</ol>\r\n\r\nA szerveremmel
  a kapcsolat meghalt (leköltözött a pincébe, kábelezés még nincs kész), így kénytelen
  voltam a desktop gépemet buherálni :). \r\nGondoltam áttérek LVM2-re, mert az összes
  teszt azt mondja, hogy az XFS jó (a reiser-rel pedig már én is szívtam), ki kéne
  próbálni, meg amúgy is lehetne jobban szervezni ezt a helyet.\r"
categories:
- linux
layout: story
author: gthomas
title: teljesen partícionált diszken lvm2-re áttérés
created: 1143301796
---
<em>Avagy hogyan lehet egy resize-t eltolni, aztán helyrehozni :)</em>


<strong>Kiindulás</strong>

Adott egy 80Gb-os winchester:
<ol>
<li>8Gb NTFS a WinXP-nek (hátha kell),</li>
<li>200Mb ext3 /boot</li>
<li>1Gb swap</li>
<li>8Gb reiser3 /</li>
<li>maradék ext2 /mnt/D (windows alól D ext2-höz való IFSD-vel)</li>
</ol>

A szerveremmel a kapcsolat meghalt (leköltözött a pincébe, kábelezés még nincs kész), így kénytelen voltam a desktop gépemet buherálni :). 
Gondoltam áttérek LVM2-re, mert az összes teszt azt mondja, hogy az XFS jó (a reiser-rel pedig már én is szívtam), ki kéne próbálni, meg amúgy is lehetne jobban szervezni ezt a helyet.


<strong>Első (rossz) lépés</strong> 

resize2fs-el az /mnt/D-t lecsökkentettem 30Gb-ra (28Gb adat van rajta) - gondoltam a felszabaduló kb. 30Gb-on elindítom az lvm-et, csinálok xfs-t a root-nak, meg kisebb reiserfs-eket mondjuk /var, /home-nak, esetleg /usr-nek...

A hibát ott követtem el, hogy töröltem a /mnt/D-nek megfelelő /dev/hda5 partíciót, majd újra létrehoztam, kisebb mérettel. A gond az, hogy a partíciók közti szabad helyet is belevette (miért is ne), így a fájlrendszer nem a partíció elején kezdődött, hanem attól mintegy 4Mb-nyira.

Próbálkoztam gpart-al (elvileg felismeri a partíciókat), de nem vált be.

Aztán jött a TestDisk, ami eleinte szemetet adott, majd egy teljes 3 órás Analyze után közölte, hogy a 16-os head helyett 255 kell neki. Ezt beállítottam, és azonnal felismerte a partíciós táblát, (mindent a helyén), kijavította a /dev/hda5-öt (valami lezáró flag kellett a végére). 

Ezek után már fel tudtam mountolni, és umount után parted-el magát a partíciót is a megfelelő méretűre tudtam szerkeszteni (azért nem ezzel indítottam, mert a fájlrendszert is méretezi, nekem akkor pedig már össze volt az csugorítva).

<strong>Helyes sorrend</strong>

Ha a parted kezeli a fájlrendszert, akkor egyszerűen parted-el resiye.
Ha nem kezeli, akkor először a megfelelő eszközzel (resize_reiserfs, xfs_growfs... etc) méretre igazítjuk a fájlrendszert, majd ezután parted-el a partíciót.

<strong>LVM</strong>
Evms-el nem kísérleteztem, mert ahhoz foltozott kernel kell.
<ol>
<li>üres partíció létrehozása</li>
<li>pvcreate /dev/hda5</li>
<li>vgcreate VG_NAME /dev/hda5</li>
<li>lvcreate -L6Gb LV_NAME VG_NAME</li>
<li>mkfs.xfs /dev/VG_NAME/LV_NAME</li>
<li>utolsó 2 lépés még akárhányszor</li>
</ol>

<strong>Csak tervezett hibák</strong>
Eddig ezek vannak meg. Tervezem, hogy 
<ol>
<li>
<code>cp --preserve=all -xr / /mnt/X</code>-al átteszem a root-ot az új helyére, bootolok <code>root=/dev/ELSO/ROOT</code>al, ha működik, akkor OK, az eddigi root is megy LVM alá mint volume;
</li><li>
Ha nem működik, akkor amit lehet átteszek LVM-ekre (/home, /usr (de legalább /usr/local), /var), a maradékot <code>resize_reiserfs</code>-al zsugorítom, és a felszabaduló hely megy LVM alá volume-nak.
</li>
</ol>

Az eredményről pedig majd beszámolok!
