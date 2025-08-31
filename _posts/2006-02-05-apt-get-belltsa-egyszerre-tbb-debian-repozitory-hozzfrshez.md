---
excerpt: "Amennyiben bosszantott már, hogy a stabil debian rendszered csomagjai már
  kicsit öregek és szeretnél újabbakat a következő kis okosság hasznos lehet számodra.
  Mivel leírom, hogy lehet megtartani a stabil alap rendszert, de már újabb debian
  csomagokat is hozzáférhetővé tenni. apt-get csomag lehtőséget ad egyszerre több
  repozitory beállítására plusz súlyozásra köztük.\r\n\r\nMegjegyzem a vegyes rendszer
  karbantartása kicsit nehézkesebb.\r\n\r\nMindösszé két konfigurációs állományt kell
  szerkesztenünk."
categories:
- debian
layout: story
author: kecsi
mail: kecsi@linuxbox.hu
title: apt-get beállítása egyszerre több debian repozitory hozzáféréséhez
created: 1139135994
---
Amennyiben bosszantott már, hogy a stabil debian rendszered csomagjai már kicsit öregek és szeretnél újabbakat a következő kis okosság hasznos lehet számodra. Mivel leírom, hogy lehet megtartani a stabil alap rendszert, de már újabb debian csomagokat is hozzáférhetővé tenni. apt-get csomag lehtőséget ad egyszerre több repozitory beállítására plusz súlyozásra köztük.

Megjegyzem a vegyes rendszer karbantartása kicsit nehézkesebb.

Mindösszé két konfigurációs állományt kell szerkesztenünk.<!--break-->
1. a jól ismert /etc/apt/sources.list állomány lehet akár a következő:
<strong>
#Stable
deb http://ftp.us.debian.org/debian stable main non-free contrib
deb http://non-us.debian.org/debian-non-US stable/non-US main contrib non-free

#Testing
deb http://ftp.us.debian.org/debian testing main non-free contrib
deb http://non-us.debian.org/debian-non-US testing/non-US main contrib non-free

#Unstable
deb http://ftp.us.debian.org/debian unstable main non-free contrib
deb http://non-us.debian.org/debian-non-US unstable/non-US main contrib non-free
</strong>
avagy az <a href="http://linuxbox.hu/public/files/sources.list">enyémhez</a> hasonló.

2. /etc/apt/preferences tartalma pedig ilyesmi:
<strong>
Package: *
Pin: release a=stable
Pin-Priority: 700

Package: *
Pin: release a=testing
Pin-Priority: 650

Package: *
Pin: release a=unstable
Pin-Priority: 600
</strong>

Ezután már használhatjuk is a testing vagy unstable csomagokat is:
Így: <strong>apt-get -t testing install <csomag></strong>
avagy így: <strong>apt-get install <csomag>/unstable</strong>
