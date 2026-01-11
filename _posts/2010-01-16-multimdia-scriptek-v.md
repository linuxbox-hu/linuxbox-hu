---
excerpt: "RGBimg2CMYKtiff: Nos, sokadik próbálgatásra sikerült egy működő változatot
  eszkábálni, csatolt file-ban megtalálható. Bár egyelőre csak monitorokon tudtam
  ellenőrizni, de gyakorlatilag ugyanazt az eredményt adja, mint a krita - csak pár
  10 másodperc alatt, guira várakozás nélkül. Ja, és ugyanaz mogrify-ra, több fájl
  egyszerre feldolgozására.\r"
categories: []
layout: blog
author: batyu
title: multimédia scriptek V.
created: 1263659722
---
RGBimg2CMYKtiff: Nos, sokadik próbálgatásra sikerült egy működő változatot eszkábálni, csatolt file-ban megtalálható. Bár egyelőre csak monitorokon tudtam ellenőrizni, de gyakorlatilag ugyanazt az eredményt adja, mint a krita - csak pár 10 másodperc alatt, guira várakozás nélkül. Ja, és ugyanaz mogrify-ra, több fájl egyszerre feldolgozására.
- egy csekély probléma, ami megoldásra vár: alfa csatornát tartalmazó képekből (pl png) megtartja az alfa csatornát a tiff-ben is -> emiatt nem pakolható a kapott tiff a tiff2pdf-el közvetlen pdf-be. Scribus dev viszont kezeli, X-1a-ra és ps-re se dob hibát a preflight, ám a kapott pdf nem teljesen az, amit várnánk, az átlátszóság a háttér előtt eltűnik, teliszínes objektumokon megmarad.


