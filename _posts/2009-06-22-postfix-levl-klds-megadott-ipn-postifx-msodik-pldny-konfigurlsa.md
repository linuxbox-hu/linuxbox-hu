---
excerpt: "Azzal a problámával találkoztam amikor egy megadott IP címen kellett volna
  kiküldeni megadott domain alól küldött leveleket. Egészen pontosan volt egy levelező
  szerverem bekonfigurálva de egy altartományt (pl levelező listák lists.pelda.hu)
  leveleit külön IP címen kellene kiküldeni. Azért merült fel erre az igény mert egyes
  szolgáltatók pl hotmail, yahoo ideiglenesen letiltanak SPAM védelmi okokból amikor
  nagy mennyiségű levelt küld ki a szerver. Szóval a megoldás kézenfekvő mozgassuk
  külön IPre a levlistákat így azok forgalma miatti problémák esetén csak a lista
  IPt tiltánák le az említett szolgáltatók a további levelezést ez nem zavarná.\r\n"
categories:
- debian
layout: story
author: kecsi
mail: kecsi@linuxbox.hu
title: Postfix levél küldés megadott IPn, postifx második példány konfigurálása
created: 1245675899
---
Azzal a problámával találkoztam amikor egy megadott IP címen kellett volna kiküldeni megadott domain alól küldött leveleket. Egészen pontosan volt egy levelező szerverem bekonfigurálva de egy altartományt (pl levelező listák lists.pelda.hu) leveleit külön IP címen kellene kiküldeni. Azért merült fel erre az igény mert egyes szolgáltatók pl hotmail, yahoo ideiglenesen letiltanak SPAM védelmi okokból amikor nagy mennyiségű levelt küld ki a szerver. Szóval a megoldás kézenfekvő mozgassuk külön IPre a levlistákat így azok forgalma miatti problémák esetén csak a lista IPt tiltánák le az említett szolgáltatók a további levelezést ez nem zavarná.
<!--break-->
Nekiláttam vizsgálódni a témában és sajnos kiderült, hogy a postfix jelen verziója(2.3-2.5) nem támogatja ezt a megoldást csak majd a még nagyon friss 2.6-os verziótól. Én a stabil verziót akartam használni és nem akartam átállni pl qmail rendszerre ezért a második postfix levelező szolgáltatás bekonfigurálása mellett döntöttem. Így két egymással párhuzamosan futó szolgáltatás futna egyazon postfix szoftverből a gépen.

A következő változtatásokat eszközöltem ehhez az eredeti levelező szolgáltatáson:
Az inet_interfaces alapértelmezett all beállítást egy IP listára cseréltam benne a lolcahost értékkel. Az smtp_bind_address pedig csak a kimenő 1 IP-re állítottam.

Majd nekiláttam a második szolgáltatás létrehozásához. Hozzunk létre másolat könyvtárakat a második postfix példány részére.
cp -rp /etc/postfix /etc/postfix2
cp -rp /var/spool/postfix /var/spool/postfix2
cp -rp /var/lib/postfix /var/lib/postfix2

Változtatások a második postfix példány main.cf konfigurációs állományán:
<code>inet_interfaces = csak_egy_IP_amin_fogadok
smtp_bind_address = csak_egy_IP_amin_küldök
alternate_config_directories = /etc/postfix2
syslog_name = postfix2
queue_directory = /var/spool/postfix2
data_directory = /var/lib/postfix2
</code>
Plusz az egyértelmű paraméter változtatások:
<code>myhostname = lists.pelda.hu
myorigin = lists.pelda.hu
mydestination = lists.pelda.hu, lista.pelda.hu</code>

mynetworks paraméterbe lehet, hogy be kell adjuk a másik (szintén itt futó) szerver IP címét ha a két szerver egymással kommunikál...

Ezután már csak egy indító szkriptet kell létrehoznunk a második példánynak vagy a egyszerűen el tudjuk indítani azt a <code>postfix -c /etc/postfix2 start</code> utasítással.

A következő apró szkript használható a második postfix példány levelező sorának megtekintésére:
<code>#!/bin/sh
export MAIL_CONFIG=/etc/postfix2
/usr/bin/mailq</code>
