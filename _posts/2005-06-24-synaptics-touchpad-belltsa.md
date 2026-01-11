---
excerpt: "Synaptics touchpad beállítása XFree86/X.org-hoz...\r\n\r\n<strong>Tulajdonságok</strong>\r\n\r\n<ul>\r\n<li>Egérmozgás
  állítható sebességgel, gyorsulással</li>\r\n<li>A pad gyors érintésével egérgombok
  emulálása</li>\r\n<li>A pad két gyors érintése a dupla kattintás</li>\r\n<li>Érintés
  és húzás a padon a mozgatás</li>\r\n<li>Középső és jobb klikk a pad felső és alsó
  szegélyénél</li>\r\n<li>Függőleges görgetés a pad jobb szegélyénél egy ujj fel-le
  húzásával (4. és 5. gomb)</li>\r\n<li>A <em>fel</em>, <em>le</em> gombok a 4. és
  5. eseményt generálják</li>\r\n<li>Vízszíntes görgetés a pad alsó szegélyénél (6.
  és 7. gomb)</li>\r\n<li>Állítható érintés érzékenység</li>\r\n<li>2 ujjal való érintés
  a középső gombot szimulálja - nem minden modellnél</li>\r\n<li>3 ujjal való érintés
  a jobb gombot szimulálja - nem minden modellnél</li>\r\n<li>Futás közbeni állítási
  lehetőség</li>\r\n<li>Abszolút és relatív pozicionálás</li>\r\n<li>A szegélyekig
  való ujjhúzás esetére beállítható, hogy úgy viselkedjem, mintha tovább húznánk az
  ujjunkat</li>\r\n</ul>\r\n\r\n"
categories:
- linux
layout: story
author: szimszon
title: Synaptics touchpad beállítása
created: 1119621993
---
Synaptics touchpad beállítása XFree86/X.org-hoz...

<strong>Tulajdonságok</strong>

<ul>
<li>Egérmozgás állítható sebességgel, gyorsulással</li>
<li>A pad gyors érintésével egérgombok emulálása</li>
<li>A pad két gyors érintése a dupla kattintás</li>
<li>Érintés és húzás a padon a mozgatás</li>
<li>Középső és jobb klikk a pad felső és alsó szegélyénél</li>
<li>Függőleges görgetés a pad jobb szegélyénél egy ujj fel-le húzásával (4. és 5. gomb)</li>
<li>A <em>fel</em>, <em>le</em> gombok a 4. és 5. eseményt generálják</li>
<li>Vízszíntes görgetés a pad alsó szegélyénél (6. és 7. gomb)</li>
<li>Állítható érintés érzékenység</li>
<li>2 ujjal való érintés a középső gombot szimulálja - nem minden modellnél</li>
<li>3 ujjal való érintés a jobb gombot szimulálja - nem minden modellnél</li>
<li>Futás közbeni állítási lehetőség</li>
<li>Abszolút és relatív pozicionálás</li>
<li>A szegélyekig való ujjhúzás esetére beállítható, hogy úgy viselkedjem, mintha tovább húznánk az ujjunkat</li>
</ul>

<!--break-->

<ol>
<li>Le kell töltenünk az X-hez a drivert: http://web.telia.com/~u89404340/touchpad/files/</li>
<li>A kernelbe be kell fordítani a <strong>CONFIG_INPUT_EVDEV</strong> eszközt.</li>
<li>A driver fordításához szükségünk lesz az x-dev, libx11-dev és libxext-dev csomagok telepítésére</li>
<li>Kicsomagolás után <strong>make</strong> és <strong>make install</strong> parancsokkal fordíthatjuk és telepíthetjük</li>
<li>A betöltendő modulok köze (X config) írjuk be: <strong>Load "synaptics"</strong></li>
<li>Készítsünk egy <strong>InpudDevice</strong> szekciót (csatolva)</li>
<li>Írjuk be a <strong>ServerLayout</strong> szekcióba: <strong>InputDevice    "Synaptics Mouse" "AlwaysCore"</strong></li>
</ol>

És kész is vagyunk.

Forrás: <a href="http://web.telia.com/~u89404340/touchpad/index.html">http://web.telia.com/~u89404340/touchpad/index.html</a>
