---
excerpt: "<h2>A megvalósításhoz szükséges\r\n</h2>\r\n<ul>\r\n  <li> swsuspend-et
  támogató kernel\r\n  <ul>\r\n    <li> CONFIG_SOFTWARE_SUSPEND=y </li>\r\n    <li>
  CONFIG_PM_STD_PARTITION=\"/dev/mapper/swap\" </li>\r\n  </ul> </li>\r\n  <li> initrd-t
  támogató kernel\r\n  <ul>\r\n    <li> CONFIG_BLK_DEV_INITRD=y </li>\r\n  </ul> </li>\r\n
  \ <li> működő initrd </li>\r"
categories:
- debian
layout: story
author: szimszon
title: Számítógép felébresztése hibernációból, titkosított swap terület és pendrive
  segítségével Debian Etch-en
created: 1178466702
---
<h2>A megvalósításhoz szükséges
</h2>
<ul>
  <li> swsuspend-et támogató kernel
  <ul>
    <li> CONFIG_SOFTWARE_SUSPEND=y </li>
    <li> CONFIG_PM_STD_PARTITION="/dev/mapper/swap" </li>
  </ul> </li>
  <li> initrd-t támogató kernel
  <ul>
    <li> CONFIG_BLK_DEV_INITRD=y </li>
  </ul> </li>
  <li> működő initrd </li>
  <li> egy titkosított swap terület és a kulcsot tartalmazó titkosított kötet a pendrive-on. (<a set="yes" href="http://wiki.hup.hu/index.php/Cryptfs_part%C3%ADci%C3%B3_felcsatol%C3%A1sa_Debianon_USBStick_seg%C3%ADts%C3%A9g%C3%A9vel_automatikusan" title="Cryptfs partíció felcsatolása Debianon USBStick segítségével automatikusan">Cryptfs partíció felcsatolása Debianon USBStick segítségével automatikusan</a>) </li>
  <li> initramfs-tools </li>
</ul>
<pre>apt-get install initramfs-tools
</pre>
<ul>
  <li> <a href="http://linux.oregpreshaz.eu/cucc/cryptresume/cryptresume" class="external" title="http://linux.oregpreshaz.eu/cucc/cryptresume/cryptresume" rel="nofollow">cryptresume</a><span class="urlexpansion"> </span>.<a href="http://linux.oregpreshaz.eu/cucc/cryptresume/cryptresume.asc" class="external" title="http://linux.oregpreshaz.eu/cucc/cryptresume/cryptresume.asc" rel="nofollow">asc</a><span class="urlexpansion">&nbsp;</span> </li>
</ul> <dl><dt>pendrive titkosítására használt kulcs</dt><dd>/etc/.penkey </dd><dt>swap titkosítására használt kulcs a pendrive-on</dt><dd>/root.key </dd><dt>pendrive device mapper neve</dt><dd> pendrive </dd><dt>swap device mapper neve</dt><dd> swap </dd></dl> <a name="initrd_testre_szab.C3.A1sa"></a>
<h2>initrd testre szabása
</h2>
<p>Másoljuk a <i>cryptresume</i> scriptet és a <i>.penkey</i>-t a <i>/etc/initramfs-tools/scripts/init-premount</i> könyvtárba:
</p>
<pre>cp cryptresume /etc/initramfs-tools/scripts/init-premount/
cp /etc/.penkey /etc/initramfs-tools/scripts/init-premount/
</pre>
<p>Nézzük át a <i>cryptresume</i> elejét és változtassuk a változók értékeit a rendszerünknek megfelelően:
</p>
<pre>PEN_KEY_FILE="/scripts/init-premount/.penkey"           # a pendrive kotet
                                                # titkositasara hasznalt kulcs
PEN_DEV="/dev/disk/by-uuid/20b56d42-3184-4036-9e17-5ad2d07273ce" # pendrive
                                                                 # particio
PEN_NAME="pendrive"             # dm pendrive neve
PEN_MOUNT_POINT="/mnt/pendrive" # pendrive kotet felcsatolasanak a helye
SWAP_KEY_FILE="root.key"        # a swap titkositasanal hasznalt kulcs
SWAP_DEV="/dev/hda2"    # fizikai swap kotet
SWAP_NAME="swap"        # dm swap neve
</pre> <a name="initrd_friss.C3.ADt.C3.A9se"></a>
<h2> initrd frissítése
</h2>
<p>Nézzük meg milyen kernelt futtatunk:
</p>
<pre>uname -a
</pre>
<p>Linux moria <b>2.6.21.moria</b> #1 Sat May 5 12:11:17 CEST 2007 i686 GNU/Linux
</p>
<p>Futtassuk az update-initramfs programot:
</p>
<pre>update-initramfs -v -u 2.6.21
</pre>
<p>Ellenőrizzük, ha LILO-t használunk, hogy a kernelünkhöz be van-e állítva az
</p>
<pre>initrd=/initrd.img
</pre>
<p>opció.
</p>
<p>Futtassuk a lilo-t:
</p>
<pre>lilo
</pre> <a name="Haszn.C3.A1lat"></a>
<h2> Használat
</h2>
<p>A kernel bootolása előtt a pendrive-ot dugjuk be az usb csatlakozóba.
</p>
<p>Az initrd futása alatt a rendszer észleli a pendrive-ot, kinyitja a pendrive titkosított kötetét, az ott talált kulcs alapján kinyitja a titkosított swap partíciót, majd megpróbálkozik a hibernált rendszer felélesztésével.
</p>
<p>Ha nem talál hibernált adatokat, akkor folytatódik a rendszer normál betöltése.
</p> 
