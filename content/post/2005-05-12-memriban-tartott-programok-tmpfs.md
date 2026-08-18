---
author: kecsi
categories:
- linux
created: 1115905410
date: '2005-05-12T00:00:00Z'
description: 'Nem tudom találkoztatok-e már a linux kernel tmpfs filerendszer szolgáltatásával. Amennyiben bekapcsoljátok a CONFIG_TMPFS kernel opciót, akkor alapból (amennyiben devfs-t használsz) a fizikai memória fele megy a /dev/shm alá mint megosztott memória terület. Természetesen ezt lehet módosítani, ha beadunk az fstab ba egy ilyen sort: tmpfs /dev/shm tmpfs defaults,size=50M 0 0 Ekkor csak egy 50 Mbyte méretű RAM drive-ot hozunk létre.'
title: Memóriában tartott programok; tmpfs
aliases:
- /node/70/
- /story/70/
---
Nem tudom találkoztatok-e már a linux kernel tmpfs filerendszer szolgáltatásával. Amennyiben bekapcsoljátok a `CONFIG_TMPFS` kernel opciót, akkor alapból (amennyiben devfs-t használsz) a fizikai memória fele megy a /dev/shm alá mint megosztott memória terület.  Természetesen ezt lehet módosítani, ha beadunk az `fstab`ba egy ilyen sort:
`tmpfs           /dev/shm        tmpfs   defaults,size=50M       0       0`
Ekkor csak egy 50 Mbyte méretű RAM drive-ot hozunk létre.
<!--break-->
Mire is lehet ezt használni?

Én például egyes kicsit lassan indúló alkalmazásokat tartok ezen a területek, amik aztán villámsebesen indulnak innét. A bootolási térképemből könnyedén ki lehet deríteni, hogy mely alkalmazás is lehet ez. :)

De van aki a /tmp vagy a /var/tmp mount pontját helyezi így memóriába, igy adva sebességnövekedési lehetőséget azon alkalmazásoknak, amelyek sokat használják ezt a területet.

tmpfs dokumentació: `/<kernel forrás>/Documentation/filesystems/tmpfs` állományban.
