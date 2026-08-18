---
author: szimszon
categories:
- linux
created: 1119621993
date: '2005-06-24T00:00:00Z'
excerpt: Synaptics touchpad beállítása XFree86/X.org-hoz... Tulajdonságok Egérmozgás állítható sebességgel, gyorsulással A pad gyors érintésével egérgombok emulálása A pad két gyors érintése a dupla kattintás Érintés és húzás a padon a mozgatás Középső és jobb klikk a pad felső és alsó szegélyénél Függőleges görgetés a pad jobb szegélyénél egy ujj fel-le húzásával (4. és 5. gomb) A fel , le gombok a 4. és 5. eseményt generálják Vízszíntes görgetés a pad alsó szegélyénél (6. és 7. gomb) Állítható érintés érzékenység 2 ujjal való érintés a középső gombot szimulálja - nem minden modellnél 3 ujjal való érintés a jobb gombot szimulálja - nem minden modellnél Futás közbeni állítási lehetőség Abszolút és relatív pozicionálás A szegélyekig való ujjhúzás esetére beállítható, hogy úgy viselkedjem, mintha tovább húznánk az ujjunkat
title: Synaptics touchpad beállítása
aliases:
- /node/81/
- /story/81/
---
Synaptics touchpad beállítása XFree86/X.org-hoz...

**Tulajdonságok**

<ul>
<li>Egérmozgás állítható sebességgel, gyorsulással</li>
<li>A pad gyors érintésével egérgombok emulálása</li>
<li>A pad két gyors érintése a dupla kattintás</li>
<li>Érintés és húzás a padon a mozgatás</li>
<li>Középső és jobb klikk a pad felső és alsó szegélyénél</li>
<li>Függőleges görgetés a pad jobb szegélyénél egy ujj fel-le húzásával (4. és 5. gomb)</li>
<li>A *fel*, *le* gombok a 4. és 5. eseményt generálják</li>
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
<li>A kernelbe be kell fordítani a `CONFIG_INPUT_EVDEV` eszközt.</li>
<li>A driver fordításához szükségünk lesz az x-dev, libx11-dev és libxext-dev csomagok telepítésére</li>
<li>Kicsomagolás után `make` és `make install` parancsokkal fordíthatjuk és telepíthetjük</li>
<li>A betöltendő modulok köze (X config) írjuk be: `Load "synaptics"`</li>
<li>Készítsünk egy `InpudDevice` szekciót (csatolva)</li>
<li>Írjuk be a `ServerLayout` szekcióba: `InputDevice    "Synaptics Mouse" "AlwaysCore"`</li>
</ol>

És kész is vagyunk.

Forrás: <a href="http://web.telia.com/~u89404340/touchpad/index.html">http://web.telia.com/~u89404340/touchpad/index.html</a>
