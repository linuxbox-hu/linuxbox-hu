---
author: kecsi
categories:
- linux
created: 1116272804
date: '2005-05-16T00:00:00Z'
excerpt: 'Sokan használjuk az alapértelmezett bash parancsfeldolgozó héjprogramot. A program a benne kiadott parancsokat .bash_history állományban eltárolja home könyvtárunkban. Az ezzel kapcsolatos ügyekedésekre hívnám most fel a figyelmet.\r\nAz arhívum tartalmát a <strong>history</strong> parannccsal tekinthetjük meg. Természetesen kereshetünk is benne egy pipe segítségével: <strong>history | grep -i keresett</strong> avagy ha a <strong>CTRL-R</strong> billentyűkombináció lenyomása után elkezdjük bebillentyűzni a keresett parancsot. Ezt a lehetőséget arhív keresési opciónak hívják. Ha nem találjuk meg a kívánt parancsot az arhívumban akkor <strong>CTRL-G</strong> vagy <strong>CTRL-C</strong>-vel megszakíthatjuk a keresést. Ha megtaláltuk a parancsot <strong>ENTER</strong>-rel azonnal futtathatjuk azt, vagy <strong>CTRL-J</strong>-vel vagy <strong>jobbra</strong> nyillal megkaphatjuk parancssorba azt további szerkesztésre.'
title: bashben kiadott parancsok arhivuma; bash history
aliases:
- /node/71/
- /story/71/
---
Sokan használjuk az alapértelmezett bash parancsfeldolgozó héjprogramot. A program a benne kiadott parancsokat .bash_history állományban eltárolja home könyvtárunkban. Az ezzel kapcsolatos ügyekedésekre hívnám most fel a figyelmet.
Az arhívum tartalmát a `history` parannccsal tekinthetjük meg. Természetesen kereshetünk is benne egy pipe segítségével: `history | grep -i keresett` avagy ha a `CTRL-R` billentyűkombináció lenyomása után elkezdjük bebillentyűzni a keresett parancsot. Ezt a lehetőséget arhív keresési opciónak hívják. Ha nem találjuk meg a kívánt parancsot az arhívumban akkor `CTRL-G` vagy `CTRL-C`-vel megszakíthatjuk a keresést. Ha megtaláltuk a parancsot `ENTER`-rel azonnal futtathatjuk azt, vagy `CTRL-J`-vel vagy **jobbra** nyillal megkaphatjuk parancssorba azt további szerkesztésre.<!--break-->
Mikor megtekintjük az arhívum tartalmát láthatjuk az egyes elemek sorszámozva vannak. Ezzel a sorszámmal is vissza tudjuk hívni az egyes  arhív sorokat újrafuttatásra a `!{sorszám}` segítségével.

További parancssori változokkal tudjuk szabályozni a teljes arhívum működését:
 <strong>export HISTFILE=/home/te_felhasznalod/.bash_history
 export HISTFILESIZE=5000
 export HISTSIZE=5000
 export HISTIGNORE='&:ls:[bf]g:exit:[ \t]*'
 export HISTCONTROL=ignoredups</strong>
Úgymint az arhívum állományának nevét, maximális sorainak számát, arhvumból kihagyandó parancsokat, duplikációk mellőzését.
A '[ \t]*' egy ügyes trükk a szóközzel kezdett parancsok kihagyását eredményezi.
Végül pedig a több soros parancsok arhívumban egy sorban tárolását a `shopt -s cmdhist` paranccsal érhetjük el.
