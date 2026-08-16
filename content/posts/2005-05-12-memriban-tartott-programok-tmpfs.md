---
author: kecsi
categories:
- linux
created: 1115905410
date: '2005-05-12T00:00:00Z'
excerpt: |
  Nem tudom találkoztatok-e már a linux kernel tmpfs filerendszer szolgáltatásával. Amennyiben bekapcsoljátok a <strong>CONFIG_TMPFS</strong> kernel opciót, akkor alapból (amennyiben devfs-t használsz) a fizikai memória fele megy a /dev/shm alá mint megosztott memória terület.  Természetesen ezt lehet módosítani, ha beadunk az <strong>fstab</strong>ba egy ilyen sort:
  <strong>tmpfs           /dev/shm        tmpfs   defaults,size=50M       0       0</strong>
  Ekkor csak egy 50 Mbyte méretű RAM drive-ot hozunk létre.
title: Memóriában tartott programok; tmpfs
---
Nem tudom találkoztatok-e már a linux kernel tmpfs filerendszer szolgáltatásával. Amennyiben bekapcsoljátok a <strong>CONFIG_TMPFS</strong> kernel opciót, akkor alapból (amennyiben devfs-t használsz) a fizikai memória fele megy a /dev/shm alá mint megosztott memória terület.  Természetesen ezt lehet módosítani, ha beadunk az <strong>fstab</strong>ba egy ilyen sort:
<strong>tmpfs           /dev/shm        tmpfs   defaults,size=50M       0       0</strong>
Ekkor csak egy 50 Mbyte méretű RAM drive-ot hozunk létre.
<!--break-->
Mire is lehet ezt használni?

Én például egyes kicsit lassan indúló alkalmazásokat tartok ezen a területek, amik aztán villámsebesen indulnak innét. A bootolási térképemből könnyedén ki lehet deríteni, hogy mely alkalmazás is lehet ez. :)

De van aki a /tmp vagy a /var/tmp mount pontját helyezi így memóriába, igy adva sebességnövekedési lehetőséget azon alkalmazásoknak, amelyek sokat használják ezt a területet.

tmpfs dokumentació: <strong>/<kernel forrás>/Documentation/filesystems/tmpfs</strong> állományban.
