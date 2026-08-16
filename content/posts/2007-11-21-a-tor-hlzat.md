---
author: szimszon
categories:
- debian
created: 1195677094
date: '2007-11-21T00:00:00Z'
title: A Tor hálózat
---
A hason című [http://hup.hu/ HUP] [http://hup.hu/node/47373 cikk] alapján...

A [http://en.wikipedia.org/wiki/Tor_%28anonymity_network%29 TOR hálózat] arra használható, hogy az ember anoním maradhasson a weben.

Hozzáadtam a sources.list-hez a következő sort:
 deb http://ftp.de.debian.org/backports.org etch-backports main contrib non-free

és telepítettem:
 apt-get install tor privoxy

[http://www.privoxy.org/ privoxy] egy proxy szerver amit együtt szoktak használni a [https://www.torproject.org/ TOR]ral. 

A '''/etc/privoxy/config''' fájlban a #-ot ki kell venni a következő sor elől:
 forward-socks4a             /     127.0.0.1:9050 .

majd újra kell indítani a proxy-t:
 /etc/init.d/privoxy restart

Ezután minden program ami képes proxy-t használni képes a [https://www.torproject.org/ TOR] hálózatát használni.

További leírás [http://gentoo-wiki.com/HOWTO_Anonymity_with_Tor_and_Privoxy itt]

Firefox kiterjesztés a [https://addons.mozilla.org/en-US/firefox/addon/2275 Torbutton] a [https://www.torproject.org/ TOR] használatának ki/bekapcsolásához (proxy kapcsolással)...
