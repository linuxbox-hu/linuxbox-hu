---
author: szimszon
categories:
- linux
created: 1117644133
date: '2005-06-01T00:00:00Z'
excerpt: |
  Ez egy egész pofás kis, <strong>konzolos</strong> jelszó kezelő program, ami a gpg-t használja fel, hogy az adatbázist titkosítsa, méghozzá az illető nyilvános kulcsával.
  
  Az adatbázis <strong>XML</strong> formában van gzippel tömörítve tárolva.
  
  A program felépítése viszonylag egyszerű, tetszőleges szintre bonthatjuk le a jelszavakat.
  Például az alapértelmezett struktúra (ami változtatható):
title: Console Password Manager
aliases:
- /node/74/
- /story/74/
---
Ez egy egész pofás kis, `konzolos` jelszó kezelő program, ami a gpg-t használja fel, hogy az adatbázist titkosítsa, méghozzá az illető nyilvános kulcsával.

Az adatbázis `XML` formában van gzippel tömörítve tárolva.

A program felépítése viszonylag egyszerű, tetszőleges szintre bonthatjuk le a jelszavakat.
Például az alapértelmezett struktúra (ami változtatható):
<!--break-->
`host -> service -> user -> password`

Amit én kiegészítettem egy **organization**-nal a <emph>/etc/cpm/cpmrc</emph> fájlban:
<code>
TemplateName "org"
TemplateName "host"
TemplateName "service"
TemplateName "user"
TemplateName "password" "password"
</code>

A programot (`cpm.bin`) egy bash script hívja meg (`cpm`), ami nekem nem szuperált igazán. Valami <emph>Memory lake</emph>-re panaszkodott, amikor bekérte a jelszót a gpg kulcsomhoz. De a
<code>
cpm.bin --key "gpg kulcs id"
</code>
tökéletesen működött.

Fiatal program, de ígéretesnek tűnik.

**Honlap:** http://www.harry-b.de/dokuwiki/doku.php?id=harry:cpm

**Debian source.list:** deb http://debian.harry-b.de/ binary/

**Gentoo ebuild:** http://debian.harry-b.de/gentoo/
