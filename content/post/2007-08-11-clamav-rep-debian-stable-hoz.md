---
author: szimszon
categories:
- debian
created: 1186826452
date: '2007-08-11T00:00:00Z'
title: Clamav repó Debian stable-hoz
aliases:
- /node/412/
- /story/412/
---
http://www.clamav.net/download/packages/packages-linux

== Debian ==
Az önkéntesek által készített csomagok frissebbek mint a distribúcióba csomagoltak,

‘’Some packages aim at fast moving targets like spam filtering and virus scanning, and even via using updated virus patterns, this doesn’t really work for the full time of a stable release.
The main issue of volatile is to allow system administrators to update their systems in a nice, consistent way without getting the drawbacks of using unstable, even without getting the drawback for the selected packages.’‘

Javasolják, hogy az alábbi repót használjuk inkább:

=== stable/etch: ===

 deb http://volatile.debian.org/debian-volatile etch/volatile main contrib non-free

Egy másik repó, amit Stefano Torricella tart karban, sid-ből visszaportolt csomagok etch-be:

http://www.y2k.it/clamav/


