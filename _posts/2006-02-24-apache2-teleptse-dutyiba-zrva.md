---
excerpt: "Megosztanám apache2 chroot-os telepítési tapasztalataim. De miért is érdemes
  vesződni a jailbe zárással. A válasz egyértelmű. A web támadók nem fognak a webszerver
  feltörése után könnyű szerrel a további dolgainkhoz férni. Természetesen ez csak
  egy újabb akadály...\r\n\r\nHát akkor készitsünk először egy alap rendszer struktúrát
  a kiválasztott jail könyvtár alá a debootstrap utsítással.\r"
categories:
- debian
layout: story
author: kecsi
mail: kecsi@linuxbox.hu
title: apache2 telepítése dutyiba zárva .)
created: 1140770209
---
Megosztanám apache2 chroot-os telepítési tapasztalataim. De miért is érdemes vesződni a jailbe zárással. A válasz egyértelmű. A web támadók nem fognak a webszerver feltörése után könnyű szerrel a további dolgainkhoz férni. Természetesen ez csak egy újabb akadály...

Hát akkor készitsünk először egy alap rendszer struktúrát a kiválasztott jail könyvtár alá a debootstrap utsítással.
 server:/#debootstrap sarge /var/apache2chroot http://ftp.hu.debian.org/debian
vagy:
 server:/#debootstrap --arch i386 sarge /var/apache2chroot

Másoljunk át, ellenőrizzünk pár fontos konfigurációs állományt:
 server:/var/apache2chroot#cp /etc/apt/sources.list /var/apache2chroot/etc/apt/sources.list
 server:/var/apache2chroot#cat /var/apache2chroot/etc/resolv.conf
 server:/var/apache2chroot#cat /var/apache2chroot/etc/hostname

Adjunk új sorokat az /etc/fstab állományunkba:
proc            /var/apache2chroot/proc proc            defaults        0       0
A tempet is fel lehet mountolni a jailbe újra, de nem kötelező.
/dev/md1        /var/apache2chroot/tmp  ext2 defaults,nodev,nosuid,noexec       0       2
Sőt a /var/www-t is akár read-only módban is ha a weboldalunk megengedi.

Mountoljuk be az előzőleg megadott pontokat:
 server:/var/apache2chroot#mount /var/apache2chroot/proc
 server:/var/apache2chroot#mount /var/apache2chroot/tmp

Nah most chroot-oljuk be magunk az új környezetünkbe:
 server:/var/apache2chroot#cd /var/apache2chroot/
 server:/var/apache2chroot#chroot .

Telepítsük fel jailen belül az apache2 csomagot és többi csomagot amit a jailben akarunk használni.
 server:/#apt-get update
 server:/#apt-get upgrade
 server:/#apt-get install apache2 libapache2-mod-php4 php4-mysql php4-ldap php4-imagick php4-gd php4-gd2 php4-pear
Ugye a fő indoka jailbe zárásnak eme utolsó csomaghalmaz sebezhetőségi pontjai. :(

Ugorjunk ki a jailből és linkeljük vissza a telepétett direket a rendes rendszerbe a későbbi könnyű kezelhetőség miatt.
 server:/#exit
 server:/var/apache2chroot#ln -s /var/apache2chroot/etc/apache2 /etc/apache2
 server:/var/apache2chroot# ln -s /var/apache2chroot/var/www/ /var/www
 server:/var/apache2chroot# ln -s /var/apache2chroot/var/log/apache2 /var/log/apache2

Csináljunk egy inditó szkriptet a jailen belüli apache indításához a külső rendszeren (ami egyszerűen bepasszolja az öszes indító paramétert a jailen belülre.):
vi /etc/init.d/apache2
#!/bin/sh -e
#
# apache2       This init.d script is used to start apache2 in jail.

case $1 in
        start)
                chroot /var/apache2chroot /etc/init.d/apache2 start
        ;;
        stop)
                chroot /var/apache2chroot /etc/init.d/apache2 stop
        ;;
        reload)
                chroot /var/apache2chroot /etc/init.d/apache2 reload
        ;;
        restart | force-reload)
                chroot /var/apache2chroot /etc/init.d/apache2 restart
        ;;
        *)
                echo "Usage: /etc/init.d/apache2 start|stop|restart|reload|force-reload"
        ;;
esac

Majd hozzuk létre rá az indító linkjeinket:
update-rc.d apache2 start 91 2 3 4 5 . stop 91 0 1 6 .

Ellenőrizhetjük h hasonlók vannak a jailen belül is amiket a debian csomag készített:
ls -l /var/apache2chroot/etc/rc*.d/*apache2

Nah mostmár konfigurálhatjuk a webszerverünk és kezdhetjük használni.

Néhány további trükk:
- a mysql szerver socketet érdemes betenni a jailbe.
 server:/etc/mysql# /etc/init.d/mysql stop
 server:/etc/mysql# mkdir /var/apache2chroot/var/run/mysqld/
 server:/etc/mysql# chown mysql.mysql /var/apache2chroot/var/run/mysqld/
 server:/etc/mysql# vi /etc/mysql/my.cnf
 server:/etc/mysql# vi /etc/mysql/debian.cnf
 server:/etc/mysql# /etc/init.d/mysql start
 server:/etc/mysql# ln -s /var/apache2chroot/var/run/mysqld/mysqld.pid /var/run/mysqld/
 server:/etc/mysql# ln -s /var/apache2chroot/var/run/mysqld/mysqld.sock /var/run/mysqld/
- levelezés működésre bírásához egy minimalista email szerver is elég a jailen belül: pl.: <a href="http://nbsmtp.ferdyx.org/">nbsmtp</a> local smarthost konfiggal. php.ini-be:
sendmail_path = nbsmtp -f info@a_te_domainod.hu -h localhost

Ne felejtsük a chroot-on belüli rendszer allományit, csomagjait is frissíteni!!!
