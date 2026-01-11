---
excerpt: "<a href=\"http://www.ietf.org/rfc/rfc4408.txt\">SPF</a> egy internet szabvány(RFC)
  arról, hogy egy megadott típusú DNS rekorddal szabályozhatjuk, hogy mely levelező
  szerver küldhet a domainünkről érkező címmel levelet.\r\nA dolog újkeletű és egyre
  több szolgáltató megköveteli, hogy ez a TXT típusú névszerver rekord létezzen a
  domainünkben.\r\n\r\nLegutóbb nekem az AOL-lal akadt össze a bajsztom a téma kapcsán.\r\n\r\nA
  rekord létrehozása egyszerű az <a href=\"http://www.openspf.org/\">openspf</a> is
  segítséget ad hozzá angolul.\r\n\r\nAz eredmény valami hasonló lesz:\r\n\r\nez a
  sor azt mondja meg, hogy a domain összes MX rekordja küldhet levelet:\r"
categories:
- linux
layout: story
author: kecsi
title: SPF (Sender Policy Framework)
created: 1148985437
---
<a href="http://www.ietf.org/rfc/rfc4408.txt">SPF</a> egy internet szabvány(RFC) arról, hogy egy megadott típusú DNS rekorddal szabályozhatjuk, hogy mely levelező szerver küldhet a domainünkről érkező címmel levelet.
A dolog újkeletű és egyre több szolgáltató megköveteli, hogy ez a TXT típusú névszerver rekord létezzen a domainünkben.

Legutóbb nekem az AOL-lal akadt össze a bajsztom a téma kapcsán.

A rekord létrehozása egyszerű az <a href="http://www.openspf.org/">openspf</a> is segítséget ad hozzá angolul.

Az eredmény valami hasonló lesz:

ez a sor azt mondja meg, hogy a domain összes MX rekordja küldhet levelet:
<code>
example.com.          86400   IN      TXT     "v=spf1 mx ?all"
</code>
ezek a rekordok pedig a MX rekordok SPF alrekordjaik, szintén szükségesek!
<code>
host1.example.com.          86400   IN      TXT     "v=spf1 a -all"
host2.example.com.          86400   IN      TXT     "v=spf1 a -all"
</code>
