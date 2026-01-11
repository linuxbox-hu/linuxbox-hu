---
excerpt: "== Hozzávalók ==\r\n\r\n* http://tunnelbroker.net/ account (egy kicsit egyszerűbb,
  mint a http://www.sixxs.net/ -nél)\r\n* Linux rendszer\r\n\r\n== Háttér ==\r\n\r\nMiután
  regisztráltunk első körben kapunk egy /64-es tartományt. De allokálhatunk egy /48-ast
  is.\r\nMindezt a „Tunnel Details” oldalon végezhetjük el.\r\n\r\nElőször is tudnunk
  kell, hogy mi az IP címünk, mivel a weblapon a tunnelt ahhoz kell beállítani (ha
  esetleg egy NAT router mögött lennénk). A tűzfalon engedni kell az ICMP-t IPv4-en
  és a 41-es protokollt.\r\n\r"
categories:
- linux
layout: story
author: szimszon
title: IPv6 konfigurálás avagy a linuxbox.hu IPv6 „Ready”
created: 1213732354
---
== Hozzávalók ==

* http://tunnelbroker.net/ account (egy kicsit egyszerűbb, mint a http://www.sixxs.net/ -nél)
* Linux rendszer

== Háttér ==

Miután regisztráltunk első körben kapunk egy /64-es tartományt. De allokálhatunk egy /48-ast is.
Mindezt a „Tunnel Details” oldalon végezhetjük el.

Először is tudnunk kell, hogy mi az IP címünk, mivel a weblapon a tunnelt ahhoz kell beállítani (ha esetleg egy NAT router mögött lennénk). A tűzfalon engedni kell az ICMP-t IPv4-en és a 41-es protokollt.

Majd a weboldal alján lehet kérni példa konfigurációt, ahol '''ifconfig'''gal:

  ifconfig sit0 up
  ifconfig sit0 inet6 tunnel ::216.66.80.30
  ifconfig sit1 up
  ifconfig sit1 inet6 add <nekünk kiosztott IPv6 cím>/64
  route -A inet6 add ::/0 dev sit1


vagy '''iproute2'''-vel:

  modprobe ipv6
  ip tunnel add he-ipv6 mode sit remote 216.66.80.30 local <local ipv4 ip*> ttl 255
  ip link set he-ipv6 up
  ip addr add <nekünk kiosztott IPv6 cím> dev he-ipv6
  ip route add ::/0 dev he-ipv6
  ip -f inet6 addr

.* az IP ha NAT tűzfal mögött vagyunk, akkor a kiosztott belső IP címnek kell lenni.

(De vannak ott meg OpenBSD, Vista és egyéb konfig ötletek)

== Az interface fájl használata (ifupdown) ==

  iface <ifname*> inet6 v4tunnel<br>
        address <nekünk kiosztott IPv6 cím><br>
        netmask 64<br>
        endpoint 216.66.80.30<br>
        local <local ipv4 ip*><br>
        up route -A inet6 add ::/0 dev <ifname><br>
        [up ip addr add <a kiosztott tartományból új IPv6 IP> dev <ifname>]<br>

.* pl.: he-ipv6

== Megvalósított példa ==

  laptop <--IPv4 openvpn tunnel--> szerver <--6in4 tunnel--> tunnelbroker <--IPv6--> IPv6 net

=== laptop ===

openvpn-nel kapcsolódik a ''server''hez.

=== IPv4 openvpn tunnel ===

Itt az openvpn egy régebben bekonfigurált IPv4-es VPN tunnel volt. Semmiféle módosítást nem igényelt.

=== szerver ===

Ez kapcsolódik egyfelől a ''laptop''hoz másfelől ide van bekonfigurálva a tunnelbroker által kiosztott tartomány. És ő működik default gw-ként a laptop IPv6-os csatlakozásához.

=== Amit kaptunk ===

;'''Tunnelbroker által delegált tartomány''': 2001:0470:1f0'''b''':71a::/64
;''' - Tunnelbroker IPv6 cím''': 2001:0470:1f0a:71a::1/64
;''' - Szerver IPv6 cím''': 2001:0470:1f0a:71a::2/64
;''' - A szerverre a szerver által kiszolgált szolgáltatásokhoz egy IPv6 cím''': 2001:0470:1f0'''b''':71a::2/64
;'''A laptop felé továbbdelegált IPv6 tartomány''': 2001:0470:1f0'''b''':71a::1:0/96
;''' - továbbdelegált tartomány szerver oldali IPv6 címe''': 2001:0470:1f0'''b''':71a::1:1/96
;''' - továbbdelegált tartomány laptop oldali IPv6 címe''': 2001:0470:1f0'''b''':71a::1:2/96
;'''Openvpn szerver oldali IPv4 cím''': 192.168.101.1
;'''Openvpn laptop oldali IPv4 cím''': 192.168.101.2

=== Szerver bekonfigurálása ===

Szerkesszük meg a ''/etc/network/interfaces'' fájl:

  0 # tunnelbroker felőli rész
  1 auto sit1
  2 iface sit1 inet6 v4tunnel
  3      address 2001:0470:1f0a:71a::2
  4      netmask 64
  5      endpoint 216.66.80.30
  6      local 212.53.166.158
  7      up route -A inet6 add ::/0 dev sit1
  8      up ip addr add 2001:470:1f0b:71a::2/64 dev sit1
  9      down ip addr del 2001:470:1f0b:71a::2/64 dev sit1

     # openvpn felőli rész
  10 auto vpn6in4
  11 iface vpn6in4 inet6 v4tunnel
  12      address 2001:0470:1f0b:71a::1:1
  13      netmask 96
  14      endpoint 192.168.101.2
  15      local 192.168.101.1

;1,10: automatikusan elindítjuk
;2,11: 6in4 tunnel definiálása ''sit1'' illetve ''vpn6in4'' névvel
;3: tunnelbroker szerver oldali IP
;4: tunnelbroker által allokált tartomány netmask-ja
;5: tunnelbroker '''IPv4''' címe
;6: szerver '''IPv4''' címe
;7: IPv6 default route a ''sit1'' interface-re
;8: szerver által kiszolgált szolgáltatásokhoz kiválasztott IP
;9: szerver által kiszolgált szolgáltatásokhoz kiválasztott IP törlése az interface-ről, ha megszüntetjük
;12: továbbdelegált tartomány szerver oldali IPv6 címe
;13: továbbdelegált tartomány netmaskja
;14: az openvpn laptop oldali '''IPv4''' címe
;15: az openvpn szerver oldali '''IPv4''' címe

  ifup sit1
  ifup vpn6in4

Ha ez sikerült, akkor eredményre kell vezetnie a
  ping6 ipv6.google.com
-nak.

=== Laptop bekonfigurálása ===

A ''/etc/network/interfaces'' fájl szerkesztése:

  1 iface vpn6in4 inet6 v4tunnel
  2      address 2001:0470:1f0b:71a::1:2
  3      netmask 96
  4      endpoint 192.168.101.1
  5      local 192.168.101.2
  6      up route -A inet6 add ::/0 dev vpn6in4

;1: 6in4 tunnel definiálása vpn6in4 névvel
;2: továbbdelegált tartomány laptop oldali IPv6 címe
;3: továbbdelegált tartomány netmaskja
;4: openvpn szerver oldali '''IPv4''' címe
;5: openvpn laptop oldali '''IPv4''' címe
;6: IPv6 default route a ''vpn6in4'' interface-re

  ifup vpn6in4

Jelenleg ez nálam működik, de mivel napközben sokmindent kézzel állítgattam, lehet, hogy a fent leírt interfaces fájl szerkesztés nem állít be mindent.

Mostmár működnie kell a
  ping6 ipv6.google.com
-nak

== Egyéb linkek ==

* http://en.wikipedia.org/wiki/Ipv6
* [http://www.fpsn.net/tools&tool=ipv6-inaddr IPv6 Reverse DNS Zone Builder for BIND 8/9] ugyanis a reverse DNS-t a tunnelbroker ki tudja delegálni.
* http://leaf.sourceforge.net/doc/bucu-ipv6.html
