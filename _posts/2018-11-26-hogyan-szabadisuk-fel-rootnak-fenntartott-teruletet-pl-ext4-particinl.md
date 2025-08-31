---
categories:
- tune2fs
layout: article
author: kecsi
mail: kecsi@linuxbox.hu
title: Hogyan szabadisuk fel rootnak fenntartott teruletet pl. EXT4 particiónál
created: 1543218161
---
Alap értelmezetten mikor fájl rendszert készítünk egy partícióra a beállítások szerint marad egy átlag felhasználó számára elérhetetlen csak root szamara fenntartott védett terület. Ez egy nagy porciónál egész tetemes lehet igy talán érdemes kisebbre bizonyos esetben akar nullara is állítani.

Igy lehet ellenőrizni mekkora területet tart fenn a rendszer erre:

```bash
sudo tune2fs -l /dev/sdb1 | grep 'Reserved block count'
```

Igy lehet változtatni pl nullara ext4 eseten:

```bash
sudo tune2fs -m 0 /dev/sdb1
```

Par szót érdemes arról megemlíteni, hogy erre a fenntartott területre akkor lehet szükség ha a fájl rendszert karbantartani kell - tehát sok állomány van azaz 95% fölött vagy közeli telitettség eseten es sok törlés új állomány létrehozásakor az állományok rendezéséhez / töredezettség mentesítéskor. Ha archívum vagy hasonló ritkán változó es jobbara csak új hozzáadott állományok eseten nyugodtan állíthatjuk ezt a fenntartott érteket nullara vagy egy kicsi értekre.

