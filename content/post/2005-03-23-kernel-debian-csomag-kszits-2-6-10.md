---
author: kecsi
categories:
- debian
created: 1111569964
date: '2005-03-23T00:00:00Z'
description: 'Kis telepítési mini jegyzet pptp számára mppe folttal, bootsplash folttal
  plusz extra nvidia modullal ellátott kernel fordítást mutat be debian rendszeren.'
title: kernel debian csomag készités 2.6.10
aliases:
- /node/5/
- /story/5/
---
*A következő kis telepítési mini jegyzet pptp számára `mppe` folttal, `bootsplash` folttal plusz extra `nvidia` modullal ellátott kernel fordítást mutat be debian rendszeren.*

Telepítsük fel a szüksélges csomagokat:
`apt-get install gcc bin86 libc6-dev bzip2 kernel-package kernel-patch-mppe kernel-source-2.6.10 tk8.3 libncurses5-dev fakeroot kernel-patch-mppe kernel-patch-bootsplash bootsplash bootsplash-theme-tuxinfo-debian`
Extra apt forrás szükséges!
```text
#bootsplash unstable
deb http://www.bootsplash.de/files/debian unstable main
deb-src http://www.bootsplash.de/files/debian unstable main
```
(/etc/apt/sources.list -hez hozzáadandó sorok)

Hát akkor hajrá, tömörítsük ki a kernel forrást:
```bash
cd /usr/src
tar xjf kernel-source-2.6.10.tar.bz2
ln -s kernel-source-2.6.10 linux
```
<!--break-->
Tegyük rá a szükséges foltokat(mivel a debian kernel forrást használjuk az már eleve sok foltot tartalmaz, lista pl itt: /usr/src/kernel-patches/all/2.6.10/debian kernel-patch-debian-2.6.10 csomagból):
```bash
cd /usr/src/linux
/usr/src/kernel-patches/all/apply/bootsplash
/usr/src/kernel-patches/all/apply/mppe
```
Konfiguráljuk be (elmentett konfigurációs állomanyból, vagy újra kézzel):
```bash
cp /boot/config-X.X.X /usr/src/linux/.config
make menuconfig
```
Amire figyelni kell:
Befordítva kell legyen a következő két kernel modul, hogy a bootsplash kód jól forduljon.
```text
CONFIG_FRAMEBUFFER_CONSOLE=y
CONFIG_FB_VESA=y
```
Egykis extra hackelés(saját extraverzió):
```text
vi Makefile
#EXTRAVERSION = -lb
#export  INSTALL_PATH=/boot
```

Készítsük el a kernel csomagunk:
`make-kpkg --initrd --revision=1 --bzimage kernel_image`
Adjuk hozzá a kiválasztott boot képernyőt az initrdnkhez:
`splash -s -f /etc/bootsplash/themes/tuxinfo-debian/config/bootsplash-1024x768.cfg >>/boot/initrd.img-2.6.10-lb`

Telepítsük fel:
lilo boot loader esetén:
```bash
vi /etc/lilo.conf
#image=/boot/vmlinuz-2.6.10-lb
#        label=lnx_2.6.10-lb
#        read-only
#        initrd=/boot/initrd.img-2.6.10-lb
#        append="splash=silent nodevfs"
#        vga=791
cd ..
dpkg -i kernel-image-2.6.10-lb_1_i386.deb
lilo
```
grub boot esetén a debian csomag teleítésekor automatikusan frissül a boot loader menübe az új kernel!
avagy `update-grub`
Ujraindítás után az X nem fog még működni először persze. jöhetnek az extra modulok pl nvidia:
```bash
apt-get install nvidia-kernel-common nvidia-glx nvidia-kernel-source
module-assistant auto-install nvidia
```
Ez az utsítás elkészít (letölt forrást, majd lefordít) egy nvidia-kernel-2.6.10-lb_1.0.7167-1+1_i386.deb csomagot és feltelepíti azt.
