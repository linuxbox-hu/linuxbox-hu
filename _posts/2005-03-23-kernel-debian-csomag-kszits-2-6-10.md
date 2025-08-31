---
excerpt: "<em>A következő kis telepítési mini jegyzet pptp számára <strong>mppe</strong>
  folttal, <strong>bootsplash</strong> folttal plusz extra <strong>nvidia</strong>
  modullal ellátott kernel fordítást mutat be debian rendszeren.</em>\r\n\r\nTelepítsük
  fel a szüksélges csomagokat:\r\n<strong>apt-get install gcc bin86 libc6-dev bzip2
  kernel-package kernel-patch-mppe kernel-source-2.6.10 tk8.3 libncurses5-dev fakeroot
  kernel-patch-mppe kernel-patch-bootsplash bootsplash bootsplash-theme-tuxinfo-debian</strong>\r\nExtra
  apt forrás szükséges!\r\n<strong>#bootsplash unstable\r\ndeb http://www.bootsplash.de/files/debian
  unstable main\r\ndeb-src http://www.bootsplash.de/files/debian unstable main</strong>\r\n(/etc/apt/sources.list
  -hez hozzáadandó sorok)\r\n\r\nHát akkor hajrá, tömörítsük ki a kernel forrást:\r\n<strong>cd
  /usr/src\r\ntar xjf kernel-source-2.6.10.tar.bz2\r\nln -s kernel-source-2.6.10 linux</strong>\r\n"
categories:
- debian
layout: story
author: kecsi
mail: kecsi@linuxbox.hu
title: kernel debian csomag készités 2.6.10
created: 1111569964
---
<em>A következő kis telepítési mini jegyzet pptp számára <strong>mppe</strong> folttal, <strong>bootsplash</strong> folttal plusz extra <strong>nvidia</strong> modullal ellátott kernel fordítást mutat be debian rendszeren.</em>

Telepítsük fel a szüksélges csomagokat:
<strong>apt-get install gcc bin86 libc6-dev bzip2 kernel-package kernel-patch-mppe kernel-source-2.6.10 tk8.3 libncurses5-dev fakeroot kernel-patch-mppe kernel-patch-bootsplash bootsplash bootsplash-theme-tuxinfo-debian</strong>
Extra apt forrás szükséges!
<strong>#bootsplash unstable
deb http://www.bootsplash.de/files/debian unstable main
deb-src http://www.bootsplash.de/files/debian unstable main</strong>
(/etc/apt/sources.list -hez hozzáadandó sorok)

Hát akkor hajrá, tömörítsük ki a kernel forrást:
<strong>cd /usr/src
tar xjf kernel-source-2.6.10.tar.bz2
ln -s kernel-source-2.6.10 linux</strong>
<!--break-->
Tegyük rá a szükséges foltokat(mivel a debian kernel forrást használjuk az már eleve sok foltot tartalmaz, lista pl itt: /usr/src/kernel-patches/all/2.6.10/debian kernel-patch-debian-2.6.10 csomagból):
<strong>cd /usr/src/linux
/usr/src/kernel-patches/all/apply/bootsplash
/usr/src/kernel-patches/all/apply/mppe</strong>
Konfiguráljuk be (elmentett konfigurációs állomanyból, vagy újra kézzel):
<strong>cp /boot/config-X.X.X /usr/src/linux/.config
make menuconfig</strong>
Amire figyelni kell:
Befordítva kell legyen a következő két kernel modul, hogy a bootsplash kód jól forduljon.
<strong>CONFIG_FRAMEBUFFER_CONSOLE=y
CONFIG_FB_VESA=y</strong>
Egykis extra hackelés(saját extraverzió):
<strong>vi Makefile
#EXTRAVERSION = -lb
#export  INSTALL_PATH=/boot</strong>

Készítsük el a kernel csomagunk:
<strong>make-kpkg --initrd --revision=1 --bzimage kernel_image</strong>
Adjuk hozzá a kiválasztott boot képernyőt az initrdnkhez:
<strong>splash -s -f /etc/bootsplash/themes/tuxinfo-debian/config/bootsplash-1024x768.cfg >>/boot/initrd.img-2.6.10-lb</strong>

Telepítsük fel:
lilo boot loader esetén:
<strong>vi /etc/lilo.conf
#image=/boot/vmlinuz-2.6.10-lb
#        label=lnx_2.6.10-lb
#        read-only
#        initrd=/boot/initrd.img-2.6.10-lb
#        append="splash=silent nodevfs"
#        vga=791
cd ..
dpkg -i kernel-image-2.6.10-lb_1_i386.deb
lilo</strong>
grub boot esetén a debian csomag teleítésekor automatikusan frissül a boot loader menübe az új kernel!
avagy <strong>update-grub</strong>
Ujraindítás után az X nem fog még működni először persze. jöhetnek az extra modulok pl nvidia:
<strong>apt-get install nvidia-kernel-common nvidia-glx nvidia-kernel-source
module-assistant auto-install nvidia</strong>
Ez az utsítás elkészít (letölt forrást, majd lefordít) egy nvidia-kernel-2.6.10-lb_1.0.7167-1+1_i386.deb csomagot és feltelepíti azt.
