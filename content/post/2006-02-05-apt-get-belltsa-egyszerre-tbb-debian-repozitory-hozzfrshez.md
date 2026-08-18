---
author: kecsi
categories:
- debian
created: 1139135994
date: '2006-02-05T00:00:00Z'
description: |-
  Amennyiben bosszantott már, hogy a stabil debian rendszered csomagjai már kicsit öregek és szeretnél újabbakat a következő kis okosság hasznos lehet számodra. Mivel leírom, hogy lehet megtartani a stabil alap rendszert, de már újabb debian csomagokat is hozzáférhetővé tenni. apt-get csomag lehtőséget ad egyszerre több repozitory beállítására plusz súlyozásra köztük.
  
  Megjegyzem a vegyes rendszer karbantartása kicsit nehézkesebb.
  
  Mindösszé két konfigurációs állományt kell szerkesztenünk.
title: apt-get beállítása egyszerre több debian repozitory hozzáféréséhez
aliases:
- /node/124/
- /story/124/
---
Amennyiben bosszantott már, hogy a stabil debian rendszered csomagjai már kicsit öregek és szeretnél újabbakat a következő kis okosság hasznos lehet számodra. Mivel leírom, hogy lehet megtartani a stabil alap rendszert, de már újabb debian csomagokat is hozzáférhetővé tenni. apt-get csomag lehtőséget ad egyszerre több repozitory beállítására plusz súlyozásra köztük.

Megjegyzem a vegyes rendszer karbantartása kicsit nehézkesebb.

Mindösszé két konfigurációs állományt kell szerkesztenünk.<!--break-->
1. a jól ismert /etc/apt/sources.list állomány lehet akár a következő:
```text
#Stable
deb http://ftp.us.debian.org/debian stable main non-free contrib
deb http://non-us.debian.org/debian-non-US stable/non-US main contrib non-free

#Testing
deb http://ftp.us.debian.org/debian testing main non-free contrib
deb http://non-us.debian.org/debian-non-US testing/non-US main contrib non-free

#Unstable
deb http://ftp.us.debian.org/debian unstable main non-free contrib
deb http://non-us.debian.org/debian-non-US unstable/non-US main contrib non-free
```
avagy az <a href="http://linuxbox.hu/public/files/sources.list">enyémhez</a> hasonló.

2. /etc/apt/preferences tartalma pedig ilyesmi:
```text
Package: *
Pin: release a=stable
Pin-Priority: 700

Package: *
Pin: release a=testing
Pin-Priority: 650

Package: *
Pin: release a=unstable
Pin-Priority: 600
```

Ezután már használhatjuk is a testing vagy unstable csomagokat is:
Így: `apt-get -t testing install <csomag>`
avagy így: `apt-get install <csomag>/unstable`
