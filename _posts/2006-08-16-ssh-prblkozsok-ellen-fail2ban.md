---
excerpt: Pár hete használom a <a href="http://fail2ban.sourceforge.net/">fail2ban</a>
  kis alkalmazást. Nagyon hatásos védekezést ad az SSH jelszó próbálgatásos támadások
  ellen. Folyamatosan olvassa az auth.log-ot és a megadott próbálkozások után iptables
  szabállyal kitiltja a próbálozó IPt. Debian csomag is létezik belőle, még sarge-ra
  is a van csomag a <a href="http://backports.org">backports.org</a>-on.
categories:
- debian
layout: story
author: kecsi
mail: kecsi@linuxbox.hu
title: 'SSH próbálkozások ellen: fail2ban'
created: 1155733692
---
Pár hete használom a <a href="http://fail2ban.sourceforge.net/">fail2ban</a> kis alkalmazást. Nagyon hatásos védekezést ad az SSH jelszó próbálgatásos támadások ellen. Folyamatosan olvassa az auth.log-ot és a megadott próbálkozások után iptables szabállyal kitiltja a próbálozó IPt. Debian csomag is létezik belőle, még sarge-ra is a van csomag a <a href="http://backports.org">backports.org</a>-on.
