---
author: szimszon
categories:
- linux
created: 1153322993
date: '2006-07-19T00:00:00Z'
description: 'Újra és újra felmerült a probléma, hogy egy IP címhez több weblap tartozik
  más névvel amihez külön ssl kulcs kellene. Tegnap talaltam egy jó leírást a http://wiki.cacert.org/wiki/VhostTaskForce-on
  ami alapján nekilelkesülve elindultam.'
title: SSL kulcs készítése Apache virtualHost-hoz Debian-on demoCA-val
aliases:
- /node/180/
- /story/180/
---
Újra és újra felmerült a probléma, hogy egy IP címhez több weblap tartozik más névvel amihez külön ssl kulcs kellene.

Ezt nem lehet kivitelezni már az ssl működése miatt sem.

Tegnap talaltam egy jó leírást a <http://wiki.cacert.org/wiki/VhostTaskForce>-on ami alapján nekilelkesülve elindultam.
<!--break-->
Lépések:

1. `cd /etc/ssl`
2. Szerkesszük meg az openssl.cnf -et
   `vim openssl.cnf`
   A lényeg:
   ```
   [ policy_anything ]
   ...
   subjectAltName = optional
   ...
   [ req ]
   ...
   x509_extensions = v3_req
   req_extensions = v3_req
   ...
   [ v3_req ]
   ...
   subjectAltName = DNS:domain.hu,DNS:vhost1.domain.hu,DNS:....
   ...
   ```
   Ahol a `domain.hu` megegyezik a `commonName`-ben megadott domain-nal is!
3. `vim /usr/lib/ssl/misc/CA.pl`
   a 138-as sort egészítsük ki a
   `system ("$CA -policy policy_anything -out newcert.pem "` -et
   `system ("$CA -policy policy_anything -out newcert.pem -extensions v3_req "` -re és mentsük el.
4. Ez után legyárthatjuk a `demoCA`-nkat (`/usr/lib/ssl/misc/CA.pl -newca`)
5. És a certeket, amik mind tartalmazni fogják a `subjectAltName`-ben megadott összes domain nevet. (`/usr/lib/ssl/misc/CA.pl -newreq; /usr/lib/ssl/misc/CA.pl -sign`)
6. A cert a `newcert.pem` fájlba kerül míg a kulcs a `newkey.pem` fájlba.
