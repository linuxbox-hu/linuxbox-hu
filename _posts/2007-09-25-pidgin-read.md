---
excerpt: "Ryan Paul munkája nyomán készült (http://arstechnica.com/reviews/apps/pidgin-2-0.ars/4)\r\n\r\nOlyan
  alkalmazás, ami feliratkozik a [http://pidgin.im pidgin] DBUS vonalára, és figyeli,
  hogy egy adott szignállal, alapértelmezetten ReceivedImMsg, milyen üzenet érkezik
  és ezt az üzenetet átadja egy parancsnak, fájl formájában vagy csőben (pipe).\r\n\r\nEzzel
  lehetőség nyílik pl. a festival-on kívül más felolvasó programot meghívni. Én az
  [http://tcts.fpms.ac.be/synthesis/mbrola.html MBROLA]-t használom...\r\n\r"
categories:
- linux
layout: story
author: szimszon
mail: szimszon@oregpreshaz.eu
title: pidgin-read
created: 1190703848
---
Ryan Paul munkája nyomán készült (http://arstechnica.com/reviews/apps/pidgin-2-0.ars/4)

Olyan alkalmazás, ami feliratkozik a [http://pidgin.im pidgin] DBUS vonalára, és figyeli, hogy egy adott szignállal, alapértelmezetten ReceivedImMsg, milyen üzenet érkezik és ezt az üzenetet átadja egy parancsnak, fájl formájában vagy csőben (pipe).

Ezzel lehetőség nyílik pl. a festival-on kívül más felolvasó programot meghívni. Én az [http://tcts.fpms.ac.be/synthesis/mbrola.html MBROLA]-t használom...

A script roppant kezdetleges, minden javítást szívesen fogadok, de nem nagyon lesz időm saját magam tovább fejleszteni :(

Mindenki használja egészséggel, de semmilyen felelősséget nem vállalok egy esetleges hibás működésből adódó káresetért.

Licenc: GPL3

 pidgin-read.py [-c <parancs>] [-f <file>] [-s <szignal>] [-p] [-h]
 ==================================================================
 
 Ryan Paul munkája nyomán készült
 (http://arstechnica.com/reviews/apps/pidgin-2-0.ars/4)
 
 v.0.1
 
 <parancs> - az a parancs amit akkor futtat le, ha a <signal>-lal
	erkezik valami (def.:/usr/local/bin/olvas)
 <file> - az a fájl amit a <parancs> megkap első paraméterként, és
	amiben benne van az érkezett szöveg. (def.:/tmp/pidgin_read.tmp)
 <szignal> - az a DBUS szignál amire a <parancs> le lesz futtatva
	(def.:ReceivedImMsg)
 -p - az üzenet szövegét nem fájlban, hanem csatornán (pipe) kapja meg
	a <parancs>
 -h - ez a képernyő


Letöltés: [https://trac.oregpreshaz.eu/cgi-bin/trac.cgi/linux/browser/src/pidgin-read/trunk/pidgin-read.py?format=raw pidgin-read.py]
