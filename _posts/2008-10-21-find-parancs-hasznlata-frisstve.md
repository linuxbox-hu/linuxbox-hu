---
excerpt: "Találtam több figyelemre méltó cikket a <a href=\"http://www.lifeaftercoffee.com/2007/04/05/using-the-find-command-in-linux-and-unix/\">find
  használatáról</a> angolul. Egy <a href=\"http://www.athabascau.ca/html/depts/compserv/webunit/HOWTO/find.htm\">másik</a>,
  egy <a href=\"http://timarcher.com/?q=node/23\">harmadik</a>.\r\nEzekből szemezgetek:\r\n<ul>Keressünk
  \r\n"
categories:
- linux
layout: story
author: kecsi
mail: kecsi@linuxbox.hu
title: find parancs használata (frissítve)
created: 1224600500
---
Találtam több figyelemre méltó cikket a <a href="http://www.lifeaftercoffee.com/2007/04/05/using-the-find-command-in-linux-and-unix/">find használatáról</a> angolul. Egy <a href="http://www.athabascau.ca/html/depts/compserv/webunit/HOWTO/find.htm">másik</a>, egy <a href="http://timarcher.com/?q=node/23">harmadik</a>.
Ezekből szemezgetek:
<ul>Keressünk 
<li>20 évnél idősebb állományokat keresünk az aktuális könyvtárban így: 
<code>find ./ -mtime +7300</code></li>
<li>az utolsó 3 napban módosított állományokat így: 
<code>find . -mtime -3.</code></li>
<li>az utolsó 3 napban módosított txt állományokat így: 
<code>find . -name '*.txt' -mtime -3</code></li>
<li>10000 kbytenál nagyobb állományokat így: 
<code>find . -size +10000k</code></li>
<li>rc.conf nevű állomány keresése az aktuális könyvtárban
<code>find . -name "rc.conf" -print </code></li>
<li>ha megtalálta a find az rc.conf nevű állományt akkor azon végre hajtja a chmod utasítást
<code>find . -name "rc.conf" -exec chmod o+r '{}' \;</code></li>
<li>komplex keresés ami kihagyja az eredményből a *.v vagy .*.v nevű állományokat. Egy kis extra magyarázat: -not negálást jelent, -o a logikai OR műveletet, \( a logikai művelet kezdetét jelöli, \) pedig a végét. Egyébként a kihagyott állományok egy verzió kezelő állományai...
<code>find /usr/src -not \( -name "*,v" -o -name ".*,v" \) '{}' \; -print</code></li>
<li>keresés a linuxbox szóra a *.html nevű állományokban, állomány név kiiratás találat esetén.
<code>find . -name "*.html" -exec grep "linuxbox" '{}' \; -print</code></li>
<li>Keresés az aktuális könyvtárból indulva kis és nagybetű nem figyelembe vételével és kihagyni a .svn nevű könyvtárak tartalmát:
<code>find . -iname "*old*" -a -not -path "*.svn*" -print</code>
Itt igazából a -and -or -not keresési feltételek közti logikai művelet megadás lehetősége a légyeg!</li>
<li>Keresés az aktuális könyvtárból indulva, csak 1 könyvtár mélységben, 1 hétnél öregebb könyvtárakat visszaadva, majd egyesével töröli. Közben listázza melyiket törli...
<code>find . -mindepth 1 -maxdepth 1 -type d -mtime +7 -exec rm -fr '{}' \; -print</code></li>
<li>Keresés csak a kezdő mount pontban pl / (root) <br/>
     <code>find / -mount -name gmetad*</code> avagy<br/> <code>find / -xdev -name gmetad*</code></li>
<li>Név alapú kizárása állományoknak és könyvtáraknak - tehát ezeket nem töröljük a végén azaz megtartjuk - csak 1 szinten keresés és az eredmény kiírása és törlése.
    <code>find /var/lib/jenkins/jobs/*/builds/*/htmlreports/* ! \( -name 'Results' -o -name 'Report' -o -name 'images' -o -name '*js' -o -name '*html' -o -name '*css' -o -name '*.png' -o -name '*.gif' -o -name '*.jpg' -o -name '*.tap' \) -maxdepth 1 -mindepth 1 -print -exec rm -fr '{}' \;</code></li>
</ul>
