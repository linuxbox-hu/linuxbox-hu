---
excerpt: "Adat cd esetén:\r\nKészítsük elő az anyagot mksisofs-sel majd írjuk fel:
  \r\n<strong> mkisofs -l -R -J -o cd.img cdre/\r\n cdrecord speed=16 dev=0,3,0 -eject
  -v a.iso<\r\n cdrecord speed=4 dev=0,3,0 -data -dao -v xp2600.iso\r\n dvdrecord
  -v -dao -eject dvdtest.bin</strong>\r\navagy\r\n<strong> cdrdao write --speed 4
  --device 0,3,0 --driver generic-mmc x.cue</strong>\r\n "
categories:
- linux
layout: story
author: kecsi
mail: kecsi@linuxbox.hu
title: Konzolos cdirás
created: 1115063467
---
Adat cd esetén:
Készítsük elő az anyagot mksisofs-sel majd írjuk fel: 
<strong> mkisofs -l -R -J -o cd.img cdre/
 cdrecord speed=16 dev=0,3,0 -eject -v a.iso<
 cdrecord speed=4 dev=0,3,0 -data -dao -v xp2600.iso
 dvdrecord -v -dao -eject dvdtest.bin</strong>
avagy
<strong> cdrdao write --speed 4 --device 0,3,0 --driver generic-mmc x.cue</strong>
 <!--break-->
audio cd esetén eljárhatunk pl. így:
<strong>cdparanoia -B "1-"
cdrecord dev=0,3,0 -eject -v -dao -audio track*
cdrecord speed=2 dev=0,3,0 -eject -v -audio track*</strong>
újraírható törlés:
<strong>cdrecord speed=4 dev=0,3,0 -eject -v blank=fast</strong>
multisession cd
<strong>NEXT_TRACK=`cdrecord -msinfo dev=1,0,0`
mkisofs -R -J -l -o cd_image2.iso -C $NEXT_TRACK -M 1,0,0 egetni_valo/
cdrecord -v dev=1,0,0 speed=4 -multi -eject cd_image2.iso</strong>
