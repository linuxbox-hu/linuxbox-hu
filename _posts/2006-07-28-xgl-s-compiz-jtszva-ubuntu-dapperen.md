---
excerpt: "Már többször olvastam cikkeket és láttam videókat  a még fejlesztés alatt
  álló <a href=\"http://hu.wikipedia.org/wiki/Xgl\">xorg XGL</a> szerveréről és a
  compizről, hogy milyen könnyen telepíthető és milyen látványos. A minap ráakadtam
  <a href=\"http://www.davehayes.org/2006/05/22/howto-xgl-and-compiz-on-ubuntu-dapper-new-and-improved\">egy
  nagyon jó telepítési leírásra</a> amit követve kb. 10 perc alatt feltelepítettem
  a fent emlegetett szoftvereket Ubuntu Dapper Drake rendszeremre. Megosztanám tapasztalataim
  most, akiket érdekel a részletes leírás olvassák tovább.\r\n"
categories:
- x
layout: story
author: kecsi
title: xgl és compiz játszva ubuntu dapperen
created: 1154072099
---
Már többször olvastam cikkeket és láttam videókat  a még fejlesztés alatt álló <a href="http://hu.wikipedia.org/wiki/Xgl">xorg XGL</a> szerveréről és a compizről, hogy milyen könnyen telepíthető és milyen látványos. A minap ráakadtam <a href="http://www.davehayes.org/2006/05/22/howto-xgl-and-compiz-on-ubuntu-dapper-new-and-improved">egy nagyon jó telepítési leírásra</a> amit követve kb. 10 perc alatt feltelepítettem a fent emlegetett szoftvereket Ubuntu Dapper Drake rendszeremre. Megosztanám tapasztalataim most, akiket érdekel a részletes leírás olvassák tovább.
<!--break--> 
Először is győződjünk meg arról, hogy X rendszerünk már felkonfigurált 3D gyorsítással bír. <a href="http://ubuntuguide.org/wiki/Dapper#Eye_Candy">Ubuntuguide is segít ebben.</a> Megjegyezném, hogy az itt leírt xgl-compiz telepítés nem tökéletes még ebben a pillanatban. 

Szóval mondjuk nvidia grafikus vezérlő kártya esetén:
Kommentezzük ki a következő sorokat a /etc/X11/xorg.conf állományból a 
<code>
Section "Module"
#	Load	"dri"
#	Load	"GLcore"
</code>
Ellenőrizzük le, hogy legyen ez a sor benne:
<code>
	Load	"glx"
</code>
A Device szekcióban a Drivert cseréljük "nv"-ről "nvidia"-ra és adjunk hozzá két új opciót. Esetleg a harmadikat is. :)
előtte:
<code>
Section "Device"
	Identifier	"NVIDIA Corporation ...."
	Driver		"nv"
	BusID		"PCI:1:0:0"
EndSection
</code> 
utána:
<code>
Section "Device"
	...
	Driver		"nvidia"
	...
	Option		"RenderAccel"		"true"
	Option		"AllowGLXWithComposite" "true"
        Option          "NoLogo"                  "true"
EndSection
</code>
Majd a screen szekcióban állítsuk az alapértelmezett színmélységet 24-re.
<code>
Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV34M [GeForce FX Go5200]"
	Monitor		"Generic Monitor"
	DefaultDepth	16
</code> itt
<code>
	DefaultDepth	24
</code> erre

Ezzel az X előkészítés meg is volna.
Most indítsuk újra az X-et. Kilépünk gdm felületre és nyomumnk egy CTRL-ALT-BACKSPACE kombinációt. Ha jó a konfig akkor nem szállt el a gdm. 8-)

Na most telepítsük fel a szoftvereket.
Adjuk be a /etc/apt/sources.list végére a következő sorokat.
<code>
deb http://www.beerorkid.com/compiz/ dapper main
deb http://xgl.compiz.info/ dapper main
deb-src http://xgl.compiz.info/ dapper main
</code>
Adjuk hozzá a csomagok ellenúrzéséhez a készítők kulcsát:
<code>
wget http://www.beerorkid.com/compiz/quinn.key.asc -O - | sudo apt-key add -
</code>
Frissítsük meg a apt-get csomag bázisát és rednszerünk.
<code>
sudo apt-get update
sudo apt-get dist-upgrade
</code>
GPG-s hibaüzenetket hagyjuk figyelmen kívül.
Most jöhet a szoftver:
<code>
sudo apt-get install compiz xserver-xgl libgl1-mesa xserver-xorg libglitz-glx1 compiz-gnome gset-compiz cgwd cgwd-themes csm
</code>
Ezzel meg is volnánk. A következő telepítési metódus abban tér el az eddig közkézre adottaktól, hogy a gdm egy új xsession-t nyit az XGL szerverrel, így egy viszonylagos biztonságot ad a fejlesztés adta stabilitási problémák ellen. Mivel ha egy frissítés után nem működik az xgl rendszer egyszerűen egy másik sessiont választunk a gdm-ben és dolgozhatunk tovább!

Szóval készítsünk egy állományt kedvenc editorunkkal:
pl:
<code>
sudo gedit /usr/bin/startxgl
</code>
A tartalma:
<code>
Xgl -fullscreen :1 -ac -accel glx:pbuffer -accel xv:pbuffer & sleep 2 && DISPLAY=:1
# Start GNOME
exec gnome-session
</code>

Adjunk rá futtatási jogot:
<code>
sudo chmod 755 /usr/bin/startxgl
</code>
Most készítsünk a gdm számára egy új session leírót:
<code>
sudo gedit /usr/share/xsessions/xgl.desktop
</code>
Evvel a tartalommal:
<code>
[Desktop Entry]
Encoding=UTF-8
Name=XGL
Exec=/usr/bin/startxgl
Icon=
Type=Application
</code>
Ha evvel kész vagyunk lépjünk ki a gdm belépési felülethez és lepjünk be újra úgy, hogy az épp elkészített "XGL" session válasszuk ki a listából.
Majd itt indítsuk el a compizt pl egy ALT-F2 futtatási ablakból.
<code>
compiz-start
</code>
Hurrá! 8-) kész vagyunk. 
Használjuk egészséggel:
    * Aktuális ablak váltása = Alt + Tab
    * Több ablak rendezése és aktuális kiválasztásának lehetősége  = F12; majd ablakra klikk
    * Kocka forgatás aka virtuális deszktop váltás = Ctrl + Alt + Balra/Jobbra nyíl
    * Virtuális deszktop váltás - az aktív ablak vonszolásával = Ctrl + Shift + Alt + Balra/Jobbra nyíl
    * Opacitás egyebek beállítása = Jobb klikk az ablak fejlécén és menüből
    ... tessék felfedezni a többit vagy az Ubuntuguide-n megkeresni... :)
