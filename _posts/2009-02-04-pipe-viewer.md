---
excerpt: "<a href=\"http://www.ivarch.com/programs/pv.shtml\">Pipe Viewer vagy csak
  egyszerűen pv</a> alkalmazás egy parancssori státusz indikátor unix pipe-ok használatához.
  \ A pipe használata mint tudjuk kicsit lassítja parancsaink végrehajtását, így nem
  feltétlen gazdaságos a dolog de sokkal látványosabb és informatívabb. :)\r\nNa lássunk
  példákat a használatára:\r\n"
categories:
- linux
layout: story
author: kecsi
mail: kecsi@linuxbox.hu
title: Pipe Viewer
created: 1233737471
---
<a href="http://www.ivarch.com/programs/pv.shtml">Pipe Viewer vagy csak egyszerűen pv</a> alkalmazás egy parancssori státusz indikátor unix pipe-ok használatához.  A pipe használata mint tudjuk kicsit lassítja parancsaink végrehajtását, így nem feltétlen gazdaságos a dolog de sokkal látványosabb és informatívabb. :)
Na lássunk példákat a használatára:
<!--break-->
Aktuális könyvtár tartalmáról tar gzip arhív készítése:
<code>$ tar -czf - . | pv > out.tgz
 117MB 0:00:55 [2.7MB/s] [>         ]</code>

Manuális postrgres db mentés és bzipelés egyben:
<code>kecsi@rivendell:~/munka/drupal/backup$ PGPASSWORD=pgpwd pg_dump -Fp -O -x -U drupal drupalDB | bzip2 | pv > dbbackup_drupalDB_`date +%Y%m%d`.dmp.bz2           14MB 0:01:06 [ 179kB/s] [                                                                                                         <=>                     ]</code>

Telepítés a legtöbb linux disztribúción pv nevű csomagként.

A unix pipe -t nem nagyon tudom lefordítani ebben is segíthettek.
Továbbá várok jópofa / látványos példákat a használatra hozzászólásként.
