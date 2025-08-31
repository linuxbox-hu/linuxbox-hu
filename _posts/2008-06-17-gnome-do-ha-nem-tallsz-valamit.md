---
excerpt: "Dicsérni fogom, pedig csak pár órája futottam véletlen bele a Gnome-do nevü
  programba. így még előjöhetnek komoly hiányosságok, de amit eddig láttam belőle...\r\n\r\n<p><a
  href=\"http://linuxbox.hu/sites/linuxbox.hu/files/gnomedo1.png\"><img src=\"http://linuxbox.hu/sites/linuxbox.hu/files/gnomedo1.png\"></a>
  </p>"
categories: []
layout: blog
author: leslie
mail: laszlo.karpati@pontez.hu
title: Gnome Do - Ha nem találsz valamit
created: 1213663994
---
Dicsérni fogom, pedig csak pár órája futottam véletlen bele a Gnome-do nevü programba. így még előjöhetnek komoly hiányosságok, de amit eddig láttam belőle...

<p><a href="http://linuxbox.hu/sites/default/files/gnomedo1.png"><img src="http://linuxbox.hu/sites/default/files/gnomedo1.png"></a> </p>

Alapvetően egy local keresőprogramról van szó. A program a háttérben fut, de gyorsbillentyűhöz rendelve (default beállítás: Super+Space) bármikor a monitorunk közepére varázsolhatjuk. Ha elkezdünk valamit begépelni, akkor azonnal megjeleníti a keresési találatokat. Hogy milyen találatokat? Plug-in kérdése: fájlok, mappák, evolution levelek, thunderbird contactok, pidgin, skype, firefox könyvjelzők, zenelejátszó, gcalendar, gcontact, system műveletek, stb...

Példának néhány érdekesség: 
Skype plugin bekapcsolás után begépeltem, hogy "online": találatként kihozta, hogy átváltoztatja Online-ra a skypeon az állapotom. (Persze amikor bekapcsoltam a plugint a skype kiírt egy üzenetet, hogy más program szeretne hozzáférni a skype irányitásához, engedélyezem-e?)

<p><a href="http://linuxbox.hu/sites/default/files/gnomedo20.jpg"><img src="http://linuxbox.hu/sites/default/files/gnomedo20.jpg"></a> </p>

Pidgin plugin bekapcsolása után begépeltem az egyik msn ismerősöm nevét: lehetőségként felkinálta, hogy cseteljek vele. Nem indítottam még el a pidgint. Kiváncsi voltam mi lesz ha így rámegyek hogy open Chat. Arra számítottam, hogy figyelmeztető ablakban felszólít majd, hogy kapcsoljam be a programot. De nem. Megnyitotta, bejelentkezett és előhívott egy chat ablakot az ismerőssel.
<p><a href="http://linuxbox.hu/sites/default/files/gnomedo21.jpg"><img src="http://linuxbox.hu/sites/default/files/gnomedo21.jpg"></a> </p>

Egyedül az zavar, hogy nem tudom, hol lehet beállítani, hogy egyszerre kettőnél több találatot mutasson. Az alapból meg nem jelenített találatokat egyelőre csak a "lefele nyíl" billentyű megnyomásával tudom elővarázsolni.

Szép a design is, de ha valaki használ compizt akkor a kereső megjelenését és elüntetését tudja feldobni az alábbi egyszerű módszerrel:
(Ez a módosítás hasonló hatással lesz a legtöbb olyan ablak megjelenésére és eltünésére, ami akkor szokott megjelenni, amikor a programok elindítása még folyamat alatt van. Más néven a splash screenekre).

Nyissuk meg az alábbi programot: 
<ul>
<li>System -> Preferences -> Advanced Desktop Effects Settings</li>
<li>Keressük az Animations effektet (kis aladinos lámpa a logója)
<p><a href="http://linuxbox.hu/sites/default/files/gnomedo10.jpg"><img src="http://linuxbox.hu/sites/default/files/gnomedo10.jpg"></a> </p>
</li>
<li>Klikk az Open Animation fülre
</li>
<li>Klikk a New-ra</li>
<li>A lenyíló fülből válasszunk egy effektet (én a Glide2-őt választottam)
</li>
<li>A durationt állítsuk valahova 200 és 400 közé</li>
<li>A window match szövehez bedig írjuk be ez: "(type=Splash)"
<p><a href="http://linuxbox.hu/sites/default/files/gnomedo11.jpg"><img src="http://linuxbox.hu/sites/default/files/gnomedo11.jpg"></a> </p>
</li>
<p><a href="http://linuxbox.hu/sites/default/files/gnomedo12.jpg"><img src="http://linuxbox.hu/sites/default/files/gnomedo12.jpg"></a> </p>

<li>Csináljuk meg ugyan ezt csak a Close Animation fülnél is. És voalá.
<p><a href="http://linuxbox.hu/sites/default/files/gnomedo13.jpg"><img src="http://linuxbox.hu/sites/default/files/gnomedo13.jpg"></a> </p>
</li>

(forrás:<a href="http://mixedbits.blogspot.com/2007/12/how-to-pimp-up-your-gnome-do.html">http://mixedbits.blogspot.com/2007/12/how-to-pimp-up-your-gnome-do.html</a>)

A legfrisseb letölthető csomag (synapticban régebbi van): 
<p><a href="http://getdeb.net/app/GNOME+Do">http://getdeb.net/app/GNOME+Do</a></p>


<code>szek.:</code> Láttam azóta tárolóban is. 
<code>
deb http://ppa.launchpad.net/do-core/ubuntu hardy main
deb-src http://ppa.launchpad.net/do-core/ubuntu hardy main
</code>

Projettel kapcsolatos oldalak / infók:
<ul>
<li>Main website: <a href="http://do.davebsd.com/">http://do.davebsd.com/</a></li>
<li>Launchpad website: <a href="https://launchpad.net/do/">https://launchpad.net/do/</a></li>
<li>IRC: #gnome-do on irc.freenode.net</li>
<li>Bugs: <a href="https://bugs.launchpad.net/do/"> https://bugs.launchpad.net/do/</a></li>
<li>Questions:<a href="https://answers.launchpad.net/do/"> https://answers.launchpad.net/do/</a></li>
<li>Mailing List:<a href="http://groups.google.com/group/gnome-do"> http://groups.google.com/group/gnome-do</a></li>
<li>Video tutorial: <a href="http://video.google.com/videoplay?docid=-9110909248380195562&hl=en"> http://video.google.com/videoplay?docid=-9110909248380195562&hl=en</a></li>
<li>Gnome Do manual (early draft): <a href="https://wiki.ubuntu.com/GnomeDo/Manual"> https://wiki.ubuntu.com/GnomeDo/Manual</a></li>
</ul>
