---
excerpt: "Samba:\r\n<strong>smbmount //tavoli.gep.nev.hu/megosztas /lokalis/konyvtar
  -o username=felhasznalonev%jelszo uid=1000 gid=104 fmask=660 dmask=750</strong>\r\n(smbfs
  csomag tartalmazza az smbmount utasitást debian disztribúcióban)\r\n\r\nFAT32 particio
  eseten <strong>/etc/fstab</strong> egy sora\r\n<strong>/dev/hda13 /winmountpoint
  vfat noexec,fat=32,uid=0,gid=50,umask=002    0       2</strong>"
categories:
- linux
layout: story
author: kecsi
mail: kecsi@linuxbox.hu
title: Samba, FAT32 mount
created: 1108675828
---
Samba:
<strong>smbmount //tavoli.gep.nev.hu/megosztas /lokalis/konyvtar -o username=felhasznalonev%jelszo uid=1000 gid=104 fmask=660 dmask=750</strong>
(smbfs csomag tartalmazza az smbmount utasitást debian disztribúcióban)

FAT32 particio eseten <strong>/etc/fstab</strong> egy sora
<strong>/dev/hda13 /winmountpoint vfat noexec,fat=32,uid=0,gid=50,umask=002    0       2</strong>
