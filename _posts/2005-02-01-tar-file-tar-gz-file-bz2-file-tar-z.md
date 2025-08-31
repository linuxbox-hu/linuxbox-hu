---
excerpt: "Kicsomagolni tar állományt: <strong>tar -xvvf file.tar</strong> (hagyd el
  a -v vagy -vv kapcsolókat ha nem akarod követni az eseményket.)\r\nMegadott kövtárba
  kicsomagolás: <strong>tar -xvf file.tar -C /destination/dir/</strong>\r\nKitömöríteni
  tar.Z állományt: <strong>tar -xvZf file.tar.Z</strong>\r\ngzippelt állományt: <strong>tar
  -xvzf file.tar.gz</strong>\r"
categories:
- linux
layout: story
author: kecsi
mail: kecsi@linuxbox.hu
title: tar, file.tar.gz, file.bz2, file.tar.Z
created: 1107254439
---
Kicsomagolni tar állományt: <strong>tar -xvvf file.tar</strong> (hagyd el a -v vagy -vv kapcsolókat ha nem akarod követni az eseményket.)
Megadott kövtárba kicsomagolás: <strong>tar -xvf file.tar -C /destination/dir/</strong>
Kitömöríteni tar.Z állományt: <strong>tar -xvZf file.tar.Z</strong>
gzippelt állományt: <strong>tar -xvzf file.tar.gz</strong>
bzippelt állományt: <strong>tar -xvjf file.tar.bz2</strong> (vagy tar -xvIf file.tar.bz2 régebbi tar esetén)
Arhiv készítés c kapcsolóval az x helyett, elõször az arhív állományt kell magadni majd utána a tömörítendõ anyagot.
pl. : <strong>tar cvvjf file.tar.bz2 /tmp/file1.kit /mashol/file2.kit /teljesdir</strong>
