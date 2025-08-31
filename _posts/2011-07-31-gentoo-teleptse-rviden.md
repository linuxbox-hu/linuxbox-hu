---
excerpt: "Ritkán de szükségem van egy friss gentoo linux telepítésre. Ilyenkor mindig
  elő kell vennem a gentoo.org oldalon található alapos, részletes dokumentációt és
  hosszasan kell olvasgatni a teendőket. Mivel gyorsan szeretek előre haladni készítettem
  egy rövid parancslistát mi a teendő.\r\n"
categories: []
layout: blog
author: siposg
mail: rg@linuxscripting.hu
title: Gentoo telepítése röviden
created: 1312118178
---
Ritkán de szükségem van egy friss gentoo linux telepítésre. Ilyenkor mindig elő kell vennem a gentoo.org oldalon található alapos, részletes dokumentációt és hosszasan kell olvasgatni a teendőket. Mivel gyorsan szeretek előre haladni készítettem egy rövid parancslistát mi a teendő.
<!--break-->
Ezek a lépések teljesen nélkülöznek minden körültekintést, megfontolást, választási lehetőséget. A lehető leggyorsabban egy működő rendszert akarok elérni. A telepítést mostanában általában virtualbox-ban hajtom végre, mert számomra tökéletesen megfelel. Ez a lépéssorozat arról szól, hogyan telepítettem utoljára virtuális gépbe.

**********
Készítsünk új virtulális gépet virtualbox alatt bridzselt hálózati kártyával, majd adjuk meg a gentoo telepítő cd iso-t: install-x86-minimal-20110322.iso
Indítsuk el a virtuális gépet és bootoljuk be a telepítőről.
**********
<strong>Kezdjük el használni a bebootolt rendszert:</strong>
<code>
net-setup eth0;dhcpcd eth0;ifconfig eth0; ping startlap.hu
/etc/init.d/sshd start
passwd</code>
**********
<strong>Gazdagépről jelentkezzünk be ssh-val:</strong>
<code>ssh root@192.168.1.100
cfdisk /dev/sda
mkfs.ext3 /dev/sda1; mkswap /dev/sda2
mount /dev/sda1 /mnt/gentoo
cd /mnt/gentoo
wget http://gentoo.inf.elte.hu/releases/x86/current-stage3/stage3-i686-20110726.tar.bz2; wget http://gentoo.inf.elte.hu/snapshots/portage-latest.tar.bz2
tar xvjpf stage3-*.tar.bz2; tar xvjf /mnt/gentoo/portage-latest.tar.bz2 -C /mnt/gentoo/usr
echo "GENTOO_MIRRORS=\"http://gentoo.inf.elte.hu/\"" >> /mnt/gentoo/etc/make.conf
cp -L /etc/resolv.conf /mnt/gentoo/etc/
mount -t proc none /mnt/gentoo/proc; mount --rbind /dev /mnt/gentoo/dev
chroot /mnt/gentoo /bin/bash</code>

<code>env-update; source /etc/profile; export PS1="(chroot) $PS1"
emerge --sync
eselect profile list; eselect profile set 2
echo "en_US.UTF-8 UTF-8" >> /etc/locale.gen; locale-gen; cp /usr/share/zoneinfo/Europe/Budapest /etc/localtime
emerge gentoo-sources; emerge genkernel; genkernel all
sed -i 's/\/dev\/BOOT/#\/dev\/BOOT/g' /etc/fstab; sed -i 's/SWAP/sda2/g' /etc/fstab; sed -i 's/ROOT/sda1/g' /etc/fstab
echo "config_eth0=( \"dhcp\" )" >> /etc/conf.d/net; cp /etc/init.d/net.lo /etc/init.d/net.eth0; rc-update add net.eth0 default; sed -i 's/localhost/gentoo/g' /etc/conf.d/hostname
passwd</code>

<code>echo "TIMEZONE=\"Europe/Budapest\"" > /etc/conf.d/clock
emerge sysklogd; emerge logrotate; rc-update add sysklogd default; emerge vixie-cron; rc-update add vixie-cron default
emerge mlocate; emerge dhcpcd; emerge grub
ls /boot/ | grep genkernel</code>

<code><em>echo "
splashimage=(hd0,0)/boot/grub/splash.xpm.gz
title Gentoo Linux 2.6.38-r6
root (hd0,0)
kernel /boot/kernel-genkernel-x86-2.6.38-gentoo-r6 real_root=/dev/sda1
initrd /boot/initramfs-genkernel-x86-2.6.38-gentoo-r6" >> /boot/grub/grub.conf</em></code>

<code>grep -v rootfs /proc/mounts > /etc/mtab; grub-install --no-floppy /dev/sda
exit
umount -l /mnt/gentoo/dev; umount -l /mnt/gentoo/proc
reboot</code>
**********
<strong>Távolítsuk el a virtuális gép CD meghajtójából az install CD imidzs fájlt és lépjünk be ssh-n:</strong>
**********
<code>ssh root@192.168.1.100
useradd -m -G users,wheel,audio -s /bin/bash proba; passwd proba
rm stage3-i686-20110726.tar.bz2; rm portage-latest.tar.bz2
echo "hu_HU UTF-8" >> /etc/locale.gen; locale-gen
emerge --sync; emerge --update --ask world</code>
**********
<strong>A gentoo alaprendszer kész, használatba lehet venni.</strong>
