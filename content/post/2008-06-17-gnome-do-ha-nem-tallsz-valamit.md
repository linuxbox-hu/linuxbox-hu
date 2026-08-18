---
author: leslie
categories: []
created: 1213663994
date: '2008-06-17T00:00:00Z'
description: Dicsérni fogom, pedig csak pár órája futottam véletlen bele a Gnome-do nevü programba. így még előjöhetnek komoly hiányosságok, de amit eddig láttam belőle...
title: 'Gnome Do - Ha nem találsz valamit'
aliases:
- /blog/525/
- /node/525/
---
Dicsérni fogom, pedig csak pár órája futottam véletlen bele a Gnome-do nevü programba. így még előjöhetnek komoly hiányosságok, de amit eddig láttam belőle...

![](/assets/img/posts/gnomedo1.png)

Alapvetően egy local keresőprogramról van szó. A program a háttérben fut, de gyorsbillentyűhöz rendelve (default beállítás: Super+Space) bármikor a monitorunk közepére varázsolhatjuk. Ha elkezdünk valamit begépelni, akkor azonnal megjeleníti a keresési találatokat. Hogy milyen találatokat? Plug-in kérdése: fájlok, mappák, evolution levelek, thunderbird contactok, pidgin, skype, firefox könyvjelzők, zenelejátszó, gcalendar, gcontact, system műveletek, stb...

Példának néhány érdekesség:
Skype plugin bekapcsolás után begépeltem, hogy "online": találatként kihozta, hogy átváltoztatja Online-ra a skypeon az állapotom. (Persze amikor bekapcsoltam a plugint a skype kiírt egy üzenetet, hogy más program szeretne hozzáférni a skype irányitásához, engedélyezem-e?)

![](/assets/img/posts/gnomedo20.jpg)

Pidgin plugin bekapcsolása után begépeltem az egyik msn ismerősöm nevét: lehetőségként felkinálta, hogy cseteljek vele. Nem indítottam még el a pidgint. Kiváncsi voltam mi lesz ha így rámegyek hogy open Chat. Arra számítottam, hogy figyelmeztető ablakban felszólít majd, hogy kapcsoljam be a programot. De nem. Megnyitotta, bejelentkezett és előhívott egy chat ablakot az ismerőssel.

![](/assets/img/posts/gnomedo21.jpg)

Egyedül az zavar, hogy nem tudom, hol lehet beállítani, hogy egyszerre kettőnél több találatot mutasson. Az alapból meg nem jelenített találatokat egyelőre csak a "lefele nyíl" billentyű megnyomásával tudom elővarázsolni.

Szép a design is, de ha valaki használ compizt akkor a kereső megjelenését és elüntetését tudja feldobni az alábbi egyszerű módszerrel:
(Ez a módosítás hasonló hatással lesz a legtöbb olyan ablak megjelenésére és eltünésére, ami akkor szokott megjelenni, amikor a programok elindítása még folyamat alatt van. Más néven a splash screenekre).

Nyissuk meg az alábbi programot:

- System -> Preferences -> Advanced Desktop Effects Settings
- Keressük az Animations effektet (kis aladinos lámpa a logója)

  ![](/assets/img/posts/gnomedo10.jpg)
- Klikk az Open Animation fülre
- Klikk a New-ra
- A lenyíló fülből válasszunk egy effektet (én a Glide2-őt választottam)
- A durationt állítsuk valahova 200 és 400 közé
- A window match szövehez bedig írjuk be ez: "(type=Splash)"

  ![](/assets/img/posts/gnomedo11.jpg)

  ![](/assets/img/posts/gnomedo12.jpg)
- Csináljuk meg ugyan ezt csak a Close Animation fülnél is. És voalá.

  ![](/assets/img/posts/gnomedo13.jpg)

(forrás: <http://mixedbits.blogspot.com/2007/12/how-to-pimp-up-your-gnome-do.html>)

A legfrisseb letölthető csomag (synapticban régebbi van):
<http://getdeb.net/app/GNOME+Do>

`szek.:` Láttam azóta tárolóban is.

```bash
deb http://ppa.launchpad.net/do-core/ubuntu hardy main
deb-src http://ppa.launchpad.net/do-core/ubuntu hardy main
```

Projettel kapcsolatos oldalak / infók:

- Main website: <http://do.davebsd.com/>
- Launchpad website: <https://launchpad.net/do/>
- IRC: #gnome-do on irc.freenode.net
- Bugs: <https://bugs.launchpad.net/do/>
- Questions: <https://answers.launchpad.net/do/>
- Mailing List: <http://groups.google.com/group/gnome-do>
- Video tutorial: <http://video.google.com/videoplay?docid=-9110909248380195562&hl=en>
- Gnome Do manual (early draft): <https://wiki.ubuntu.com/GnomeDo/Manual>
