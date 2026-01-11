---
layout: post
title: Virtualbox vdi átméretezés (windows host, linux guest using LVM and xfs)
date: 2015-10-27
author: kecsi
categories: [linux]
tags: 
 - virtualbox
 - fdisk
 - LVM
 - pvresize
 - lvresize
 - mount
 - xfs
 - xfs_growfs
excerpt: Amikor a virtualbox particionkon elfogy a hely gondolkodhatunk, hogy megnagyobbitjuk
  vagy beadunk egy ujabb particiót...

---
Amikor a virtualbox particionkon elfogy a hely gondolkodhatunk, hogy megnagyobbitjuk vagy beadunk egy ujabb particiót. Én a komplikáltabb nagyobbítást választottam:
(ha nem gond angolul hagyom a procedura lépéseit, valószínűleg így is érthetőek mindenki számára aki ilyesmivel dolgozik.)

- Shutdown guest
- Resize dvi using vboxmanage to 86G
  `VBoxManage modifyhd c:\VirtualBoxVMs\my_OL7.1\my_OL7.1-01.vdi --resize 88064`
- start up guest
- `umount /u01`
- delete and recreate partition
  `fdisk /dev/sda`
   delete sda2, recreate with new size, keep/change type 8e
- reboot guest to make partition table changes live
- `umount /u01` 
- `pvresize /dev/sda2`
- `lvresize -l +100%FREE /dev/mapper/ol-home`
- `mount /u01`
- `xfs_growfs /dev/mapper/ol-home`
