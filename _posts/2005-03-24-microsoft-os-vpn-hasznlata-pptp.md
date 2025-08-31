---
excerpt: "Amennyiben a munkahelyi belső hálózatot csak m$ VPN-en keresztül éred el
  a pptp használatát ajánlom.\r\n\r\nElőször is szükséged lesz az előző kernel készítés
  cikkben is emlegett mmpe kernel foltra és még jópár másik alap kernel modulra. Egészen
  pontosan:\r\n<strong>ip_gre, ppp_mppe, ppp_deflate, sha1, arc4</strong>\r\n\r\nEzután
  jöhet a kapcsolatot és minden mást kezelő pptpconfig és az általa használt util
  csomag telpítése:\r\n\r\npptpconfig extra apt forrásból szerezhető csak be egyenlőre:\r\n<strong>#
  James Cameron's PPTP GUI packaging\r\ndeb http://quozl.netrek.org/pptp/pptpconfig
  ./</strong>\r"
categories:
- debian
layout: story
author: kecsi
mail: kecsi@linuxbox.hu
title: Microsoft-os VPN használata; pptp
created: 1111702838
---
Amennyiben a munkahelyi belső hálózatot csak m$ VPN-en keresztül éred el a pptp használatát ajánlom.

Először is szükséged lesz az előző kernel készítés cikkben is emlegett mmpe kernel foltra és még jópár másik alap kernel modulra. Egészen pontosan:
<strong>ip_gre, ppp_mppe, ppp_deflate, sha1, arc4</strong>

Ezután jöhet a kapcsolatot és minden mást kezelő pptpconfig és az általa használt util csomag telpítése:

pptpconfig extra apt forrásból szerezhető csak be egyenlőre:
<strong># James Cameron's PPTP GUI packaging
deb http://quozl.netrek.org/pptp/pptpconfig ./</strong>
(/etc/apt/source.list -hez hozzáadandó sorok)

A valódi telepítés:
<strong>apt-get install pptp-linux pptpconfig</strong>

A konfigurálás innét már értelemszerű! (A Routing fül kitöltése nálam szükséges volt a működéshez.)

További info angolul <a href="http://pptpclient.sourceforge.net/howto-debian.phtml">itt</a>.
