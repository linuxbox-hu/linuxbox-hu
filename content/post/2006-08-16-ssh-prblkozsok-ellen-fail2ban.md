---
author: kecsi
categories:
- debian
created: 1155733692
date: '2006-08-16T00:00:00Z'
description: Pár hete használom a fail2ban kis alkalmazást. Nagyon hatásos védekezést ad az SSH jelszó próbálgatásos támadások ellen. Folyamatosan olvassa az auth.log-ot és a megadott próbálkozások után iptables szabállyal kitiltja a próbálozó IPt. Debian csomag is létezik belőle, még sarge-ra is a van csomag a backports.org -on.
title: 'SSH próbálkozások ellen: fail2ban'
aliases:
- /node/188/
- /story/188/
---
Pár hete használom a <a href="http://fail2ban.sourceforge.net/">fail2ban</a> kis alkalmazást. Nagyon hatásos védekezést ad az SSH jelszó próbálgatásos támadások ellen. Folyamatosan olvassa az auth.log-ot és a megadott próbálkozások után iptables szabállyal kitiltja a próbálozó IPt. Debian csomag is létezik belőle, még sarge-ra is a van csomag a <a href="http://backports.org">backports.org</a>-on.
