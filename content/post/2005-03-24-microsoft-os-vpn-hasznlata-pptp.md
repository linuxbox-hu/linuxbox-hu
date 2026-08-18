---
author: kecsi
categories:
- debian
created: 1111702838
date: '2005-03-24T00:00:00Z'
description: 'Amennyiben a munkahelyi belső hálózatot csak m$ VPN-en keresztül éred el a pptp használatát ajánlom. Először is szükséged lesz az előző kernel készítés cikkben is emlegett mmpe kernel foltra és még jópár másik alap kernel modulra. Egészen pontosan: ip_gre, ppp_mppe, ppp_deflate, sha1, arc4 Ezután jöhet a kapcsolatot és minden mást kezelő pptpconfig és az általa használt util csomag telpítése: pptpconfig extra apt forrásból szerezhető csak be egyenlőre: # James Cameron''s PPTP GUI packaging deb http://quozl.netrek.org/pptp/pptpconfig ./'
title: Microsoft-os VPN használata; pptp
aliases:
- /node/49/
- /story/49/
---
Amennyiben a munkahelyi belső hálózatot csak m$ VPN-en keresztül éred el a pptp használatát ajánlom.

Először is szükséged lesz az előző kernel készítés cikkben is emlegett mmpe kernel foltra és még jópár másik alap kernel modulra. Egészen pontosan:
`ip_gre, ppp_mppe, ppp_deflate, sha1, arc4`

Ezután jöhet a kapcsolatot és minden mást kezelő pptpconfig és az általa használt util csomag telpítése:

pptpconfig extra apt forrásból szerezhető csak be egyenlőre:
```text
# James Cameron's PPTP GUI packaging
deb http://quozl.netrek.org/pptp/pptpconfig ./
```
(/etc/apt/source.list -hez hozzáadandó sorok)

A valódi telepítés:
`apt-get install pptp-linux pptpconfig`

A konfigurálás innét már értelemszerű! (A Routing fül kitöltése nálam szükséges volt a működéshez.)

További info angolul <a href="http://pptpclient.sourceforge.net/howto-debian.phtml">itt</a>.
