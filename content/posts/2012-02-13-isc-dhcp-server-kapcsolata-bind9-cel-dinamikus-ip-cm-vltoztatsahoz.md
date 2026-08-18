---
author: szimszon
categories:
- linux
created: 1329164430
date: '2012-02-13T00:00:00Z'
excerpt: '...avagy szegény ember saját dyndns-e.'
title: isc-dhcp-server kapcsolata bind9-cel dinamikus IP cím változtatásahoz...
aliases:
- /node/708/
- /story/708/
---
...avagy szegény ember saját dyndns-e.

Persze szegény embernek van egy [tp-link](http://www.tp-link.com) vagy [dlink](http://www.dlink.com) routere, amin beállítja a megfelelő résznél, hogy milyen hozzáférési adatokkal tud beállítani egy ip-t egy megadott domain névhez.

Ez a leírás nem erről szól. Itt szükség van egy [bind9](http://www.bind9.net/) dns szerverre és [isc-dhcp-server](http://www.isc.org/software/dhcp)re. Miért is? Pl. van valahol egy olcsó kis tárhellyel rendelkező szerverünk amin saját magunknak üzemeltetünk dns szervert. És van egy elfogadható sebességű internet kapcsolatunk és egy szerver a speizban, ami éjjel nappal megy :) Ez a lekvárok között helyet foglaló szerver dhcp-n keresztül kap ip címet, ami meg-megváltozik. Hát jól üzenjük meg ezt a bind-nek.

A leírás [ezen](http://ops.ietf.org/dns/dynupd/secure-ddns-howto.html) alapul.

A dns szerver mellett hozzunk létre egy kulcsot ami az egyik dns zónánk *(example.com)* egyik aldomainjéhez fog tartozni *(thorin.example.com)*.

```bash
dnssec-keygen -r /dev/urandom -a RSAMD5 -b 1024 -T KEY -n ZONE thorin.example.com.
```

Ezennel eldöntöttük, hogy *thorin* barátunk lesz felhatalmazva a változások ismertetésére. A fenti parancs lefuttatásával valami ilyen fájlokat kapunk:

```
Kthorin.example.com.+001+06581.key
Kthorin.example.com.+001+06581.private
```

A *.... .key* fájlt azon melegébe hozzá is cat-olhatjuk a zóna fájlunkhoz. Ne felejtsük el növelni a szériaszámát a zónának! Nos ezzel a lépéssel lehetővé tettük hogy thorin később igazolja magát a dns felé és kérjen változásokat a zónában.

Hát azért legyünk óvatosak és csak azt engedjük amit szeretnénk:

A *named.conf.local* fájlban kicsit bővítsük ki a zónára vonatkozó beállításokat:

```
zone "example.com" {
        type master;
        file "/etc/bind/db.example.com";
        update-policy {
                grant thorin.example.com. name gollam.example.com. A TXT;
        };
};
```

Máris megengedtük *thorin* barátunknak, hogy *gollam.example.com* A és TXT rekordját módosítsa.

Szerver kész. Most koncentráljunk a dhcp-re.

Másoljuk át mindkét dnssec-kel készített kulcsot a */etc/dhcp/keys* könyvtárba. Ezután már csak egy rövid teendőnk van. A */etc/dhcp/dhclient-exit-hooks.d* könyvtárba másoldjuk be a következő scriptet:

```bash
ZONE=example.com
HOSTNAME=gollam.example.com
KEYFILE=/etc/dhcp/keys/Kthorin.example.com.+001+06581.private
nsupdate -v -k "$KEYFILE" > /dev/null <<EOF
server $SERVER
zone $ZONE
update delete $HOSTNAME A
update add $HOSTNAME $TTL A $new_ip_address
send
EOF
E=$?
logger -t "dhclient" "Uj IP ($new_ip_address) lekuldve az example.com-nak. [$E]"
exit $E
```

Sajnos jelenleg (Debian Squeeze-en) az nsupdate egy hatalmas hibaüzenettel lép ki. Ez

```
mem.c:1099: INSIST(ctx->stats[i].gets == 0U) failed, back trace
#0 0xb73f6e27 in ??
#1 0xb73f7093 in ??
#2 0xb740aa33 in ??
#3 0xb740ad35 in ??
#4 0xb77b8819 in ??
#5 0xb7172ca6 in ??
#6 0xb77b1801 in ??
/etc/dhcp/dhclient-exit-hooks.d/update: line 25: 19652 Aborted
```

sajnos normális, az A rekord ettől függetlenül frissült.

Viola. Kész is vagyunk.
