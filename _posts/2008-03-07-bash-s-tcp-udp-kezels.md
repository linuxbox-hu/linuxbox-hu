---
excerpt: "A <a href=\"http://hup.hu/node/51963\">HUP-on</a> olvastam, hogy a Bash
  gond nélkül képes kezelni tcp és udp kapcsolatokat\r\n(socketen keresztül).  Kicsit
  utánajártam a dolognak, így találtam egy nagyon jó <a href=\"http://shudder.daemonette.org/source/BashNP-Guide.txt\">leírást</a>\r\n(igaz
  angol nyelven), ami a működés hátterét is bemutatja.\r\nA <a href=\"http://tldp.org/LDP/abs/html/devref1.html\">másik
  leírás</a> a TLDP projectből való ami további példákat is tartalmaz.\r\n\r"
categories:
- linux
layout: story
author: Goosfrabaa
mail: gabrea@freemail.hu
title: Bash és tcp/udp kezelés
created: 1204895446
---
A <a href="http://hup.hu/node/51963">HUP-on</a> olvastam, hogy a Bash gond nélkül képes kezelni tcp és udp kapcsolatokat
(socketen keresztül).  Kicsit utánajártam a dolognak, így találtam egy nagyon jó <a href="http://shudder.daemonette.org/source/BashNP-Guide.txt">leírást</a>
(igaz angol nyelven), ami a működés hátterét is bemutatja.
A <a href="http://tldp.org/LDP/abs/html/devref1.html">másik leírás</a> a TLDP projectből való ami további példákat is tartalmaz.

Úgy tűnik a Debian alapú disztribúciók (?) <a href="http://thesmithfam.org/blog/2006/05/23/bash-socket-programming-with-devtcp-2/#comment-4847">nem támogatják</a> a bash ezen funkciójának használatát.
