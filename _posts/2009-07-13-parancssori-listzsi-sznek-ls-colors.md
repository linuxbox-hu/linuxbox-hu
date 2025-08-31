---
excerpt: "Ha valaki sötét háttérszínű terminált használ lehet, hogy a listázási színeket
  testre kell szabja, hogy könnyebben olvasható színes listákat kapjon, ha használja
  ezt a szolgáltatást. A következőekben be szeretném mutatni, hogyan kell beállítani/módosítani
  a parancssoros listázás színeit.\r\n"
categories:
- linux
layout: story
author: kecsi
mail: kecsi@linuxbox.hu
title: Parancssori listázási színek; ls colors
created: 1247489152
---
Ha valaki sötét háttérszínű terminált használ lehet, hogy a listázási színeket testre kell szabja, hogy könnyebben olvasható színes listákat kapjon, ha használja ezt a szolgáltatást. A következőekben be szeretném mutatni, hogyan kell beállítani/módosítani a parancssoros listázás színeit.
<!--break-->
Előkészületképp futtassuk le a következő utasításokat melyekkel megvizsgáljuk, hogy a jelenlegi beállításainkban van-e álnév(alias) definiálva az ls utasításhoz és kiiratjuk a jelenlegi LS_COLORS változónk ha van ilyen.
<code>alias ls
echo $LS_COLORS</code>

Ezeken a változtatás vagy ezek definiálása egyszerű a következő két utasítással. Később ha elégedettek vagyunk az eredménnyel hozzáadhatjuk ezeket a parancsokat pl a ~/.bashrc állományba, így rögzítve a jövőbeni használathoz...
<code>alias ls='ls --color'
LS_COLORS='di=1:fi=0:ln=31:pi=5:so=5:bd=5:cd=5:or=31:mi=0:ex=35:*.rpm=90'
export LS_COLORS</code>
De mit is futtatunk itt?

Az első ls álnév bevezetésével azt definiáljuk hogy a jövőben a listázást állandóan a --color paraméterrel akarjuk futtatni azaz színes listázást kérünk.
A második és harmadik utasítás definiálja az LS_COLORS parancssori változót amelynek kettősponttal elválasztott tagjai a következők:
di = könyvtár
fi = állomány
ln = link
pi = fifo állomány
so = socket állomány
bd = blokk eszköz
cd = karakter eszköz
or = hibás link (elárvult azaz nincs meg az állomány amire mutatott anno)
mi = hiángyzó állomány?
ex = futtatható állomány

A végén pedig definiálható megadott kiterjesztásű állományok különböző színe is pl. itt az RPM csomagokat definiáljuk *.rpm=90 parmáterrel a 90-es (sötét szürke) színhez.

ui: eredeti angol cikk <a href="http://www.linux-sxs.org/housekeeping/lscolors.html">itt</a>.

ui: végezetül néhány konkrét példa
pl. redhat ES4 alapbállítása a következő ami néhány típusnál putty-ban elég nehezen olvasható:
<code>user@server:~> echo $LS_COLORS
no=00:fi=00:di=00;34:ln=00;36:pi=40;33:so=00;35:bd=40;33;01:cd=40;33;01:or=01;05;37;41:mi=01;05;37;41:ex=00;32:*.cmd=00;32:*.exe=00;32:*.com=00;32:*.btm=00;32:*.bat=00;32:*.sh=00;32:*.csh=00;32:*.tar=00;31:*.tgz=00;31:*.arj=00;31:*.taz=00;31:*.lzh=00;31:*.zip=00;31:*.z=00;31:*.Z=00;31:*.gz=00;31:*.bz2=00;31:*.bz=00;31:*.tz=00;31:*.rpm=00;31:*.cpio=00;31:*.jpg=00;35:*.gif=00;35:*.bmp=00;35:*.xbm=00;35:*.xpm=00;35:*.png=00;35:*.tif=00;35:</code>
pl. a debian 5 sokkal jobban olvasható ilyen szempontból
<code>myuser@myserver:~$ echo $LS_COLORS
no=00:fi=00:di=01;34:ln=01;36:pi=40;33:so=01;35:do=01;35:bd=40;33;01:cd=40;33;01:or=40;31;01:su=37;41:sg=30;43:tw=30;42:ow=34;42:st=37;44:ex=01;32:*.tar=01;31:*.tgz=01;31:*.svgz=01;31:*.arj=01;31:*.taz=01;31:*.lzh=01;31:*.lzma=01;31:*.zip=01;31:*.z=01;31:*.Z=01;31:*.dz=01;31:*.gz=01;31:*.bz2=01;31:*.bz=01;31:*.tbz2=01;31:*.tz=01;31:*.deb=01;31:*.rpm=01;31:*.jar=01;31:*.rar=01;31:*.ace=01;31:*.zoo=01;31:*.cpio=01;31:*.7z=01;31:*.rz=01;31:*.jpg=01;35:*.jpeg=01;35:*.gif=01;35:*.bmp=01;35:*.pbm=01;35:*.pgm=01;35:*.ppm=01;35:*.tga=01;35:*.xbm=01;35:*.xpm=01;35:*.tif=01;35:*.tiff=01;35:*.png=01;35:*.svg=01;35:*.mng=01;35:*.pcx=01;35:*.mov=01;35:*.mpg=01;35:*.mpeg=01;35:*.m2v=01;35:*.mkv=01;35:*.ogm=01;35:*.mp4=01;35:*.m4v=01;35:*.mp4v=01;35:*.vob=01;35:*.qt=01;35:*.nuv=01;35:*.wmv=01;35:*.asf=01;35:*.rm=01;35:*.rmvb=01;35:*.flc=01;35:*.avi=01;35:*.fli=01;35:*.gl=01;35:*.dl=01;35:*.xcf=01;35:*.xwd=01;35:*.yuv=01;35:*.aac=00;36:*.au=00;36:*.flac=00;36:*.mid=00;36:*.midi=00;36:*.mka=00;36:*.mp3=00;36:*.mpc=00;36:*.ogg=00;36:*.ra=00;36:*.wav=00;36:</code>
