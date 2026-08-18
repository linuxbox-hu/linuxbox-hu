---
author: kecsi
categories:
- linux
created: 1107254439
date: '2005-02-01T00:00:00Z'
excerpt: 'Kicsomagolni tar állományt: <strong>tar -xvvf file.tar</strong> (hagyd el a -v vagy -vv kapcsolókat ha nem akarod követni az eseményket.)\r\nMegadott kövtárba kicsomagolás: <strong>tar -xvf file.tar -C /destination/dir/</strong>\r\nKitömöríteni tar.Z állományt: <strong>tar -xvZf file.tar.Z</strong>\r\ngzippelt állományt: <strong>tar -xvzf file.tar.gz</strong>\r'
title: tar, file.tar.gz, file.bz2, file.tar.Z
aliases:
- /node/11/
- /story/11/
---
Kicsomagolni tar állományt: `tar -xvvf file.tar` (hagyd el a -v vagy -vv kapcsolókat ha nem akarod követni az eseményket.)
Megadott kövtárba kicsomagolás: `tar -xvf file.tar -C /destination/dir/`
Kitömöríteni tar.Z állományt: `tar -xvZf file.tar.Z`
gzippelt állományt: `tar -xvzf file.tar.gz`
bzippelt állományt: `tar -xvjf file.tar.bz2` (vagy tar -xvIf file.tar.bz2 régebbi tar esetén)
Arhiv készítés c kapcsolóval az x helyett, elõször az arhív állományt kell magadni majd utána a tömörítendõ anyagot.
pl. : `tar cvvjf file.tar.bz2 /tmp/file1.kit /mashol/file2.kit /teljesdir`
