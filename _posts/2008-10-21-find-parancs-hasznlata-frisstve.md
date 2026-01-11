---
title: find parancs használata (frissítve)
description: Példák hogyan használom a find parancsot...
author: kecsi
date: 2008-10-21 11:33:00 +0800
permalink: /find
categories: [linux, utils]
tags: [find]
pin: false
math: false
mermaid: false
image:
  path: /assets/img/posts/find-example.png
---
## find parancs használata

Példák hogyan használom a find parancsot...

```bash
# pl. 20 évnél idősebb állományokat keresünk az aktuális könyvtárban így: 
find . -mtime +7300

# az utolsó 3 napban módosított állományokat így: 
find . -mtime -3

# az utolsó 3 napban módosított txt állományokat így: 
find . -name '*.txt' -mtime -3

# 10000 kbytenál nagyobb állományokat így: 
find . -size +10000k

# rc.conf nevű állomány keresése az aktuális könyvtárban
find . -name "rc.conf" -print

# ha megtalálta a find az rc.conf nevű állományt akkor azon végre hajtja a chmod utasítást
find . -name "rc.conf" -exec chmod o+r '{}' \;

# komplex keresés ami kihagyja az eredményből a *.v vagy .*.v nevű állományokat. Egy kis extra magyarázat: -not negálást jelent, -o a logikai OR műveletet, \( a logikai művelet kezdetét jelöli, \) pedig a végét. Egyébként a kihagyott állományok egy verzió kezelő állományai...
find /usr/src -not \( -name "*,v" -o -name ".*,v" \) '{}' \; -print

# keresés a linuxbox szóra a *.html nevű állományokban, állomány név kiiratás találat esetén.
find . -name "*.html" -exec grep "linuxbox" '{}' \; -print

# Keresés az aktuális könyvtárból indulva kis és nagybetű nem figyelembe vételével és kihagyni a .svn nevű könyvtárak tartalmát:
find . -iname "*old*" -a -not -path "*.svn*" -print

# Itt igazából az -and -or -not keresési feltételek közti logikai művelet megadás lehetősége a légyeg.
# Keresés az aktuális könyvtárból indulva, csak 1 könyvtár mélységben (-mindepth 1 -maxdepth 1),
# 1 hétnél öregebb (-mtime +7) könyvtárakat (-type d) visszaadva, majd egyesével töröli (exec rm -fr '{}' \;)
# Közben listázza is amelyikeket törli (-print)
find . -mindepth 1 -maxdepth 1 -type d -mtime +7 -exec rm -fr '{}' \; -print

# Keresés csak a kezdő mount pontban pl / (root) 
find / -mount -name gmetad*
# avagy
find / -xdev -name gmetad*

# Név alapú kizárása állományoknak és könyvtáraknak - tehát ezeket nem töröljük a végén azaz megtartjuk - csak 1 szinten keresés és az eredmény kiírása és törlése.
find /var/lib/jenkins/jobs/*/builds/*/htmlreports/* ! \( -name 'Results' -o -name 'Report' -o -name 'images' -o -name '*js' -o -name '*html' -o -name '*css' -o -name '*.png' -o -name '*.gif' -o -name '*.jpg' -o -name '*.tap' \) -maxdepth 1 -mindepth 1 -print -exec rm -fr '{}' \;
```