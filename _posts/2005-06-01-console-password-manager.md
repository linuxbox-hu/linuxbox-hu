---
excerpt: "Ez egy egész pofás kis, <strong>konzolos</strong> jelszó kezelő program,
  ami a gpg-t használja fel, hogy az adatbázist titkosítsa, méghozzá az illető nyilvános
  kulcsával.\r\n\r\nAz adatbázis <strong>XML</strong> formában van gzippel tömörítve
  tárolva.\r\n\r\nA program felépítése viszonylag egyszerű, tetszőleges szintre bonthatjuk
  le a jelszavakat.\r\nPéldául az alapértelmezett struktúra (ami változtatható):\r\n"
categories:
- linux
layout: story
author: szimszon
mail: szimszon@oregpreshaz.eu
title: Console Password Manager
created: 1117644133
---
Ez egy egész pofás kis, <strong>konzolos</strong> jelszó kezelő program, ami a gpg-t használja fel, hogy az adatbázist titkosítsa, méghozzá az illető nyilvános kulcsával.

Az adatbázis <strong>XML</strong> formában van gzippel tömörítve tárolva.

A program felépítése viszonylag egyszerű, tetszőleges szintre bonthatjuk le a jelszavakat.
Például az alapértelmezett struktúra (ami változtatható):
<!--break-->
<strong>host -> service -> user -> password</strong>

Amit én kiegészítettem egy <strong>organization</strong>-nal a <emph>/etc/cpm/cpmrc</emph> fájlban:
<code>
TemplateName "org"
TemplateName "host"
TemplateName "service"
TemplateName "user"
TemplateName "password" "password"
</code>

A programot (<strong>cpm.bin</strong>) egy bash script hívja meg (<strong>cpm</strong>), ami nekem nem szuperált igazán. Valami <emph>Memory lake</emph>-re panaszkodott, amikor bekérte a jelszót a gpg kulcsomhoz. De a
<code>
cpm.bin --key "gpg kulcs id"
</code>
tökéletesen működött.

Fiatal program, de ígéretesnek tűnik.

<strong>Honlap:</strong> http://www.harry-b.de/dokuwiki/doku.php?id=harry:cpm

<strong>Debian source.list:</strong> deb http://debian.harry-b.de/ binary/

<strong>Gentoo ebuild:</strong> http://debian.harry-b.de/gentoo/
