---
categories: []
layout: blog
author: bAndie91
title: óraátállítás (emuláció)
created: 1269717257
---
<!--break--><!--break-->Bizonytalan vagyok, hogy mikor, merre, melyik idozónában, melyik párhuzamos multiverzumban hány fokkal kell idoszámításunkat eltolni. Szerencsére a rendszerprogramozók tudják <!--break-->(ha maguk nem is, de programjaik), ezért csak egyszeruen ki kell nyerni az információkat. Így:

# d=`date +%s`;
# vagy nemsokkal a lehetséges (hajnali 2..3 óra) váltópont elé tekerjük
d=`date +%s -d "00:00 2010-03-28"`
# a számláló (33 másodpercesével, hogy látványos legyen)
while true; do echo -ne "`date -d @$d`\r"; d=$(($d+33)); done

Váltott is az CET idozóna CEST-re!
