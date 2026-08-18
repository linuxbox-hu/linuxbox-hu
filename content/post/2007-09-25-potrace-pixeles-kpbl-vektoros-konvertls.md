---
author: log69
categories: []
created: 1190740387
date: '2007-09-25T00:00:00Z'
description: 'Amikor egy pixelekből álló képet nagyítani szeretnénk, akkor több rossz megoldás közül választhatunk; vagy minél élesebb és széttörtebb lesz a képünk, vagy homályosabb de annál természetesebb. Sajnos általában egyik sem megoldás. Ha a bitkép nem tartalmaz sok színt, akkor lehetőség van egy ún. Trace eljárásra, ami a pixeles képet vektorossá alakítja.'
title: 'Potrace - pixeles képből vektoros konvertálás'
aliases:
- /blog/437/
- /node/437/
---
Amikor egy pixelekből álló képet nagyítani szeretnénk, akkor több rossz megoldás közül választhatunk; vagy minél élesebb és széttörtebb lesz a képünk, vagy homályosabb de annál természetesebb. Sajnos általában egyik sem megoldás. Ha a bitkép nem tartalmaz sok színt, akkor lehetőség van egy ún. Trace eljárásra, ami a pixeles képet vektorossá alakítja. Ennek tulajdonsága, hogy végtelen finomságú lesz mivel a képen található íveket és rajzokat görbékkel próbálja meg leírni / közelíteni.

Én a megoldásra létező és elérhető szoftverek közül kipróbáltam nagyon sokat (ha nem az összeset), és a legjobbnak a [Potrace](http://potrace.sourceforge.net) neveztű kicsi parancssori alkalmazást találtam. A legtöbb program (akár fizetős) általában egy kisfelbontású képnél egy csúcsot jellemző résznél lekerekített eredményt adott, holott a vektorban hegyes csúcsnak kellett volna lennie. Potrace meglepően jó eredménnyel szolgált.

<http://potrace.sourceforge.net>

Az [Inkscape](http://www.inkscape.org) nevű vektorgrafikus program is a Potrace-t használja egyébként (Path / Trace Bitmap menü Shift+Alt+B). Potrace sajnos nem támogat png formátumot bemenetként, de ez nem akadály, bármelyik képnézegető vagy grafikus programból könnyedén menthetünk agy pbm vagy bmp formátumot.

```bash
~$ potrace -s image.bmp
```

Eredeti bemenet:

![](/assets/img/posts/test_orig.png)

![](/assets/img/posts/test_zoom.png)

Kimenet:

![](/assets/img/posts/test_result.png)

A programnak hátránya a fizetős nagyobb programokkal szemben, hogy csak 1 színű képet tud vektorizálni. Ha több színt tartalmaz a kép, akkor egy ún. [Treshold](http://en.wikipedia.org/wiki/Adaptive_thresholding) eljárással azt kettő színessé alakítja (szürkévé konvertálja majd egy bizonyos szint alatt és felett a színeket feketévé és fehérré alakítja).
