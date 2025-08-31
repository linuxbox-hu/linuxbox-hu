---
excerpt: "<p><a title=\"http://syncthing.net/\" target=\"_blank\" href=\"http://syncthing.net/\">Syncthing</a>
  multi platformos, <a title=\"https://github.com/calmh/syncthing/blob/master/protocol/PROTOCOL.md\"
  target=\"_blank\" href=\"https://github.com/calmh/syncthing/blob/master/protocol/PROTOCOL.md\">nyílt
  kódú</a> fájl szinkronizáló megoldás <a title=\"http://www.bittorrent.com/sync\"
  target=\"_blank\" href=\"http://www.bittorrent.com/sync\">BTSync</a> helyett.</p>\r\n"
categories:
- hírek
layout: story
author: szimszon
mail: szimszon@oregpreshaz.eu
title: Syncthing
created: 1403097342
---
<p><a title="http://syncthing.net/" target="_blank" href="http://syncthing.net/">Syncthing</a> multi platformos, <a title="https://github.com/calmh/syncthing/blob/master/protocol/PROTOCOL.md" target="_blank" href="https://github.com/calmh/syncthing/blob/master/protocol/PROTOCOL.md">nyílt kódú</a> fájl szinkronizáló megoldás <a title="http://www.bittorrent.com/sync" target="_blank" href="http://www.bittorrent.com/sync">BTSync</a> helyett.</p>
<!--break-->
<p><img src="http://syncthing.net/screenshot.png" align="bottom" />&nbsp;
</p>
<p>A fejlesztő <a title="https://discourse.syncthing.net/t/security-principles/48" target="_blank" href="https://discourse.syncthing.net/t/security-principles/48">elmondása</a> szerint biztonság és az adatok védelme az elsődleges cél.
</p>
<p>Jelenleg még nem tart az 1-es verziónál, de ígéretes sebességben megy a <a title="https://discourse.syncthing.net/t/release-schedule/45" target="_blank" href="https://discourse.syncthing.net/t/release-schedule/45">fejlesztés</a>.
</p>
<p>Az alábbi rendszereken futtatható:
</p>
<ul>
  <li> Mac </li>
  <li> Windows </li>
  <li> Linux </li>
  <li> BSD </li>
  <li> Solaris </li>
</ul>
<p>A programot <a title="http://golang.org/" target="_blank" href="http://golang.org/">Go</a>-ban írják és a fejlesztés a <a title="http://github.com/calmh/syncthing" target="_blank" href="http://github.com/calmh/syncthing">Github</a>-on van. A kezelői felülete weblap.
  <br />
</p>
<p>Működését tekintve a gépek közötti kapcsolatot <a title="https://en.wikipedia.org/wiki/Transport_Layer_Security" target="_blank" href="https://en.wikipedia.org/wiki/Transport_Layer_Security">TLS</a>-sel titkosítja.&nbsp; A <a title="https://discourse.syncthing.net/t/how-node-ids-work/365" target="_blank" href="https://discourse.syncthing.net/t/how-node-ids-work/365">gépek (node) egyéni azonosítót kapnak</a>, egy 52 karakteres kódot amik azonosítják a hálózaton. Helyi hálózaton belül üzenetszórással (UDP 21025-ös port) értesítik elérhetőségükről a kliensek egymást. Egyéb esetben IP, gépnév (DNS) vagy bekapcsolható a „global discovery”, amikor a „global discovery service”-re a node ID és a külső port elérés beregisztrálásra kerül, ami lekérdezhető, találják meg egymást a gépek. A <a title="https://discourse.syncthing.net/t/firewalls-and-port-forwards/166/3" target="_blank" href="https://discourse.syncthing.net/t/firewalls-and-port-forwards/166/3">tűzfal</a> (TCP 22000-ös port) beállításában az <a title="https://en.wikipedia.org/wiki/Universal_Plug_and_Play" target="_blank" href="https://en.wikipedia.org/wiki/Universal_Plug_and_Play">UPnP</a> segít.
</p>
<p>Jelenleg 1 millió fájl lehet egy kötetben és egy fájl kb. max. 12GiB lehet. Valamint egyenlőre a fájl index a memóriában tárolódik. Ld.: <a title="https://discourse.syncthing.net/t/frequently-asked-questions-faq/405" target="_blank" href="https://discourse.syncthing.net/t/frequently-asked-questions-faq/405">GYIK</a>&nbsp;
  <br />
</p>
<p>Indulásnak érdemes elolvasni a „<a title="https://discourse.syncthing.net/t/getting-started/46" target="_blank" href="https://discourse.syncthing.net/t/getting-started/46">Getting Started</a>” leírást.
</p>
<p>Amit érdemes észben tartani, hogy minden gépen minden minden klienst fel kell venni kézzel és a szinkronizálandó köteteket egyező ID-val fel kell venni mindenhol.
</p>
<p><a title="http://discourse.syncthing.net/" target="_blank" href="http://discourse.syncthing.net/">Beszélgetések</a> :: <a title="http://discourse.syncthing.net/category/documentation" target="_blank" href="http://discourse.syncthing.net/category/documentation">Leírások</a> :: <a title="https://github.com/calmh/syncthing/releases/latest" target="_blank" href="https://github.com/calmh/syncthing/releases/latest">Letöltések</a> :: <a title="http://github.com/calmh/syncthing" target="_blank" href="http://github.com/calmh/syncthing">Fejlesztés</a>
  <br />
</p>
