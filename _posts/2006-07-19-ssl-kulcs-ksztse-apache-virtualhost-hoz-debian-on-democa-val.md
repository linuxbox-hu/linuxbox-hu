---
excerpt: "<p>Újra és újra felmerült a probléma, hogy egy IP címhez több weblap tartozik
  más névvel amihez külön ssl kulcs kellene. \r\n</p> \r\n<p>&nbsp;Ezt nem lehet kivitelezni
  már az ssl működése miatt sem. \r\n</p> \r\n<p>Tegnap talaltam egy jó leírást a
  <a title=\"http://wiki.cacert.org/wiki/VhostTaskForce\" target=\"_blank\" href=\"http://wiki.cacert.org/wiki/VhostTaskForce\">http://wiki.cacert.org/wiki/VhostTaskForce</a>
  -on ami alapján nekilelkesülve elindultam. \r\n</p> "
categories:
- linux
layout: story
author: szimszon
title: SSL kulcs készítése Apache virtualHost-hoz Debian-on demoCA-val
created: 1153322993
---
<p>Újra és újra felmerült a probléma, hogy egy IP címhez több weblap tartozik más névvel amihez külön ssl kulcs kellene. 
</p> 
<p>&nbsp;Ezt nem lehet kivitelezni már az ssl működése miatt sem. 
</p> 
<p>Tegnap talaltam egy jó leírást a <a title="http://wiki.cacert.org/wiki/VhostTaskForce" target="_blank" href="http://wiki.cacert.org/wiki/VhostTaskForce">http://wiki.cacert.org/wiki/VhostTaskForce</a> -on ami alapján nekilelkesülve elindultam. 
</p> <!--break--> 
<p> Lépések: 
</p> 
<ol> 
  <li><font face="courier new,courier,monospace">cd /etc/ssl</font> 
  </li> 
  <li>Szerkesszük meg az openssl.cnf -et 
    <br /><font face="courier new,courier,monospace">vim openssl.cnf</font> 
    <br />A lényeg: 
    <br />
    <hr size="2" width="100%" />
    <br /> 
    <blockquote><font face="courier new,courier,monospace">[ policy_anything ]</font> 
      <br /><font face="courier new,courier,monospace">... 
      <br />subjectAltName = optional 
      <br />... 
      <br />[ req ] 
      <br />... 
      <br />x509_extensions = v3_req 
      <br />req_extensions = v3_req 
      <br />... 
      <br />[ v3_req ] 
      <br />... 
      <br />subjectAltName = DNS:domain.hu,DNS:vhost1.domain.hu,DNS:.... 
      <br />...</font> 
      <br />
    </blockquote>
    <br />
    <hr size="2" width="100%" />
    <blockquote> 
    </blockquote>Ahol a <b>domain.hu</b> megegyezik a <b>commonName</b>-ben megadott domain-nal is! 
    <br />
  </li>
  <li><font face="courier new,courier,monospace">vim /usr/lib/ssl/misc/CA.pl
    <br /></font>a 138-as sort egészítsük ki a
    <br /><font face="courier new,courier,monospace">system ("$CA -policy policy_anything -out newcert.pem "</font> -et
    <br /><font face="courier new,courier,monospace">system ("$CA -policy policy_anything -out newcert.pem <b>-extensions v3_req </b>"</font> -re és mentsük el.
  </li>
  <li>Ez után legyárthatjuk a <b>demoCA</b>-nkat (<font face="courier new,courier,monospace">/usr/lib/ssl/misc/CA.pl -newca</font>)
  </li>
  <li>És a certeket, amik mind tartalmazni fogják a <b>subjectAltName</b>-ben megadott összes domain nevet. (<font face="courier new,courier,monospace">/usr/lib/ssl/misc/CA.pl -newreq; /usr/lib/ssl/misc/CA.pl -sign</font>)
  </li>
  <li>A cert a <b>newcert.pem</b> fájlba kerül míg a kulcs a <b>newkey.pem</b> fájlba.
    <br />
  </li> 
</ol> 
