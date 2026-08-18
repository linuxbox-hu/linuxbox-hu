---
author: kecsi
categories:
- linux
created: 1108675828
date: '2005-02-17T00:00:00Z'
excerpt: 'Samba: smbmount //tavoli.gep.nev.hu/megosztas /lokalis/konyvtar -o username=felhasznalonev%jelszo uid=1000 gid=104 fmask=660 dmask=750 (smbfs csomag tartalmazza az smbmount utasitást debian disztribúcióban) FAT32 particio eseten /etc/fstab egy sora /dev/hda13 /winmountpoint vfat noexec,fat=32,uid=0,gid=50,umask=002 0 2'
title: Samba, FAT32 mount
aliases:
- /node/30/
- /story/30/
---
Samba:
`smbmount //tavoli.gep.nev.hu/megosztas /lokalis/konyvtar -o username=felhasznalonev%jelszo uid=1000 gid=104 fmask=660 dmask=750`
(smbfs csomag tartalmazza az smbmount utasitást debian disztribúcióban)

FAT32 particio eseten `/etc/fstab` egy sora
`/dev/hda13 /winmountpoint vfat noexec,fat=32,uid=0,gid=50,umask=002    0       2`
