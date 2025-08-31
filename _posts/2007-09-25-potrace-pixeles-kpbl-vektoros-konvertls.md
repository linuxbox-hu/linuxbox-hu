---
excerpt: "Amikor egy pixelekből álló képet nagyítani szeretnénk, akkor több rossz
  megoldás közül választhatunk; vagy minél élesebb és széttörtebb lesz a képünk, vagy
  homályosabb de annál természetesebb. Sajnos általában egyik sem megoldás. Ha a bitkép
  nem tartalmaz sok színt, akkor lehetőség van egy ún. Trace eljárásra, ami a pixeles
  képet vektorossá alakítja. Ennek tulajdonsága, hogy végtelen finomságú lesz mivel
  a képen található íveket és rajzokat görbékkel próbálja meg leírni / közelíteni.\r\n\r"
categories: []
layout: blog
author: log69
mail: han@log69.com
title: Potrace - pixeles képből vektoros konvertálás
created: 1190740387
---
Amikor egy pixelekből álló képet nagyítani szeretnénk, akkor több rossz megoldás közül választhatunk; vagy minél élesebb és széttörtebb lesz a képünk, vagy homályosabb de annál természetesebb. Sajnos általában egyik sem megoldás. Ha a bitkép nem tartalmaz sok színt, akkor lehetőség van egy ún. Trace eljárásra, ami a pixeles képet vektorossá alakítja. Ennek tulajdonsága, hogy végtelen finomságú lesz mivel a képen található íveket és rajzokat görbékkel próbálja meg leírni / közelíteni.

Én a megoldásra létező és elérhető szoftverek közül kipróbáltam nagyon sokat (ha nem az összeset), és a legjobbnak a <a href="http://potrace.sourceforge.net">Potrace</a> neveztű kicsi parancssori alkalmazást találtam. A legtöbb program (akár fizetős) általában egy kisfelbontású képnél egy csúcsot jellemző résznél lekerekített eredményt adott, holott a vektorban hegyes csúcsnak kellett volna lennie. Potrace meglepően jó eredménnyel szolgált.

<a href="http://potrace.sourceforge.net">http://potrace.sourceforge.net</a>

Az <a href="http://www.inkscape.org">Inkscape</a> nevű vektorgrafikus program is a Potrace-t használja egyébként (Path / Trace Bitmap menü Shift+Alt+B). Potrace sajnos nem támogat png formátumot bemenetként, de ez nem akadály, bármelyik képnézegető vagy grafikus programból könnyedén menthetünk agy pbm vagy bmp formátumot.

~$ potrace -s image.bmp

Eredeti bemenet:
<img src="/sites/default/files/test_orig.png" />

<img src="/sites/default/files/test_zoom.png" />

Kimenet:
<img src="/sites/default/files/test_result.png" />

A programnak hátránya a fizetős nagyobb programokkal szemben, hogy csak 1 színű képet tud vektorizálni. Ha több színt tartalmaz a kép, akkor egy ún. <a href="http://en.wikipedia.org/wiki/Adaptive_thresholding">Treshold</a> eljárással azt kettő színessé alakítja (szürkévé konvertálja majd egy bizonyos szint alatt és felett a színeket feketévé és fehérré alakítja).
