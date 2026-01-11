---
excerpt: "<p>...avagy szegény ember saját dyndns-e.\r\n</p>"
categories:
- linux
layout: story
author: szimszon
title: isc-dhcp-server kapcsolata bind9-cel dinamikus IP cím változtatásahoz...
created: 1329164430
---
<p>...avagy szegény ember saját dyndns-e.
</p>
<p>Persze szegény embernek van egy <a title="http://www.tp-link.com" target="_blank" href="http://www.tp-link.com">tp-link</a> vagy <a title="http://www.dlink.com" target="_blank" href="http://www.dlink.com">dlink</a> routere, amin beállítja a megfelelő résznél, hogy milyen hozzáférési adatokkal tud beállítani egy ip-t egy megadott domain névhez.
</p>
<p>Ez a leírás nem erről szól. Itt szükség van egy <a title="http://www.bind9.net/" target="_blank" href="http://www.bind9.net/">bind9</a> dns szerverre és <a title="http://www.isc.org/software/dhcp" target="_blank" href="http://www.isc.org/software/dhcp">isc-dhcp-server</a>re. Miért is? Pl. van valahol egy olcsó kis tárhellyel rendelkező szerverünk amin saját magunknak üzemeltetünk dns szervert. És van egy elfogadható sebességű internet kapcsolatunk és egy szerver a speizban, ami éjjel nappal megy :) Ez a lekvárok között helyet foglaló szerver dhcp-n keresztül kap ip címet, ami meg-megváltozik. Hát jól üzenjük meg ezt a bind-nek.
</p>
<p>A leírás <a title="http://ops.ietf.org/dns/dynupd/secure-ddns-howto.html" target="_blank" href="http://ops.ietf.org/dns/dynupd/secure-ddns-howto.html">ezen</a> alapul.
</p>
<p>A dns szerver mellett hozzunk létre egy kulcsot ami az egyik dns zónánk <em>(example.com)</em> egyik aldomainjéhez fog tartozni <em>(thorin.example.com)</em>.
</p>
<p><font face="courier new,courier,monospace"># dnssec-keygen -r /dev/urandom -a RSAMD5 -b 1024 -T KEY -n ZONE thorin.example.com.</font>
</p>
<p>Ezennel eldöntöttük, hogy <em>thorin</em> barátunk lesz felhatalmazva a változások ismertetésére. A fenti parancs lefuttatásával valami ilyen fájlokat kapunk:
</p>
<p><font face="courier new,courier,monospace">Kthorin.example.com.+001+06581.key
  <br />Kthorin.example.com.+001+06581.private</font>
</p>
<p>&nbsp;A <em>.... .key</em> fájlt azon melegébe hozzá is cat-olhatjuk a zóna fájlunkhoz. Ne felejtsük el növelni a szériaszámát a zónának! Nos ezzel a lépéssel lehetővé tettük hogy thorin később igazolja magát a dns felé és kérjen változásokat a zónában.
</p>
<p>Hát azért legyünk óvatosak és csak azt engedjük amit szeretnénk:
</p>
<p>&nbsp;A <em>named.conf.local</em> fájlban kicsit bővítsük ki a zónára vonatkozó beállításokat:
</p>
<p><font face="courier new,courier,monospace">zone "example.com" {
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; type master;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; file "/etc/bind/db.example.com";
<strong>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; update-policy {
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; grant thorin.example.com. name gollam.example.com. A TXT;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; };
</strong>};</font>
</p>
<p>Máris megengedtük <em>thorin</em> barátunknak, hogy <em>gollam.example.com</em>&nbsp; A és TXT rekordját módosítsa.
  <br />
</p>
<p> Szerver kész. Most koncentráljunk a dhcp-re.
</p>
<p>&nbsp;Másoljuk át mindkét dnssec-kel készített kulcsot a<em> /etc/dhcp/keys </em>könyvtárba. Ezután már csak egy rövid teendőnk van. A <em>/etc/dhcp/dhclient-exit-hooks.d</em> könyvtárba másoldjuk be a következő&nbsp; scriptet:
</p>
<p><font face="courier new,courier,monospace">ZONE=example.com
HOSTNAME=gollam.example.com
KEYFILE=/etc/dhcp/keys/Kthorin.example.com.+001+06581.private<br/>
nsupdate -v -k "$KEYFILE" &gt; /dev/null &lt;&lt;EOF
server $SERVER
zone $ZONE
update delete $HOSTNAME A
update add $HOSTNAME $TTL A $new_ip_address
send
EOF<br/>
E=$?
logger -t "dhclient" "Uj IP ($new_ip_address) lekuldve az example.com-nak. [$E]"
exit $E</font>
</p>
<p>Sajnos jelenleg (Debian Squeeze-en) az nsupdate egy hatalmas hibaüzenettel lép ki. Ez
</p>
<p><font face="courier new,courier,monospace">mem.c:1099: INSIST(ctx-&gt;stats[i].gets == 0U) failed, back trace
#0 0xb73f6e27 in ??
#1 0xb73f7093 in ??
#2 0xb740aa33 in ??
#3 0xb740ad35 in ??
#4 0xb77b8819 in ??
#5 0xb7172ca6 in ??
#6 0xb77b1801 in ??
/etc/dhcp/dhclient-exit-hooks.d/update: line 25: 19652 Aborted</font>
</p>
<p>sajnos normális, az A rekord ettől függetlenül frissült.
</p>
<p>&nbsp;Viola. Kész is vagyunk.
  <br />
</p>
