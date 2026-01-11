---
excerpt: "Ezt a technikát még nem ismertem, pedig pofon egyszerű. \r\nUgye az interneten
  használt nevek feloldásakor az operációs rendszerek így a linux is használnak egy
  statikus hosts állományt(/etc/hosts) is. Ha mi egy nem kívánt weboldal nevét a localhost
  IPjével(127.0.0.1) betesszük ebbe az állományba akkor arra az oldalra a böngészőnkből
  többé még véletlen se tévedünk. :)\r\n\r"
categories:
- linux
layout: story
author: kecsi
title: Reklámok és egyéb nemkívánatos weboldalak blokkolása /etc/hosts állománnyal
created: 1253267192
---
Ezt a technikát még nem ismertem, pedig pofon egyszerű. 
Ugye az interneten használt nevek feloldásakor az operációs rendszerek így a linux is használnak egy statikus hosts állományt(/etc/hosts) is. Ha mi egy nem kívánt weboldal nevét a localhost IPjével(127.0.0.1) betesszük ebbe az állományba akkor arra az oldalra a böngészőnkből többé még véletlen se tévedünk. :)

Vannak akik odáig elmennek, hogy az internetre csatlakozó routerükre telepítenek apró szkripteket amik megadott indőközönként letöltenek és frissítenek nem kívánatos címek listáját több gyűjteményből. Íme a <a href="http://www.linksysinfo.org/forums/showthread.php?p=323869">linksysinfo.org-on</a> egy kis segédlet, szkript az előbb emlegetett megoldáshoz(Angolul).

Persze mindezt mi magunk linuxon asztali gépünkön is megtehetjük így érdemesnek látom a hosts állományok hozzáférését átmásolni/lefordítani az előző oldalról:
<ul><li>MVPS HOSTS file: <a href="http://www.mvps.org/winhelp2002/hosts.txt" target="_blank">http://www.mvps.org/winhelp2002/hosts.txt</a> (~18,500 bejegyzés, 680 Kbyte)</li>
<li>PGL YOYO: <a href="http://pgl.yoyo.org/adservers/serverlist.php?hostformat=hosts" target="_blank">http://pgl.yoyo.org/adservers/server...stformat=hosts</a> (~2,200 bejegyzés, 68 Kbyte)</li>

<li>hosts-file.net: <a href="http://www.it-mate.co.uk/downloads/hosts.txt" target="_blank">http://www.it-mate.co.uk/downloads/hosts.txt</a> (~53,000 bejegyzés, 1.5 Mbyte)</li>
<li>The Hosts File Project: <a href="http://hostsfile.mine.nu/Hosts" target="_blank">http://hostsfile.mine.nu/Hosts</a> (~102,000 bejegyzés, 3.0 Mbyte)</li>
</ul>
