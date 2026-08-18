---
author: szimszon
categories:
- debian
created: 1178466702
date: '2007-05-06T00:00:00Z'
title: Számítógép felébresztése hibernációból, titkosított swap terület és pendrive segítségével Debian Etch-en
aliases:
- /node/368/
- /story/368/
---
## A megvalósításhoz szükséges

- swsuspend-et támogató kernel
  - CONFIG_SOFTWARE_SUSPEND=y
  - CONFIG_PM_STD_PARTITION="/dev/mapper/swap"
- initrd-t támogató kernel
  - CONFIG_BLK_DEV_INITRD=y
- működő initrd
- egy titkosított swap terület és a kulcsot tartalmazó titkosított kötet a pendrive-on. ([Cryptfs partíció felcsatolása Debianon USBStick segítségével automatikusan](http://wiki.hup.hu/index.php/Cryptfs_part%C3%ADci%C3%B3_felcsatol%C3%A1sa_Debianon_USBStick_seg%C3%ADts%C3%A9g%C3%A9vel_automatikusan))
- initramfs-tools

```bash
apt-get install initramfs-tools
```

- [cryptresume](http://linux.oregpreshaz.eu/cucc/cryptresume/cryptresume).[asc](http://linux.oregpreshaz.eu/cucc/cryptresume/cryptresume.asc)
- **pendrive titkosítására használt kulcs**: /etc/.penkey
- **swap titkosítására használt kulcs a pendrive-on**: /root.key
- **pendrive device mapper neve**: pendrive
- **swap device mapper neve**: swap

## initrd testre szabása

Másoljuk a `cryptresume` scriptet és a `.penkey`-t a `/etc/initramfs-tools/scripts/init-premount` könyvtárba:

```bash
cp cryptresume /etc/initramfs-tools/scripts/init-premount/
cp /etc/.penkey /etc/initramfs-tools/scripts/init-premount/
```

Nézzük át a `cryptresume` elejét és változtassuk a változók értékeit a rendszerünknek megfelelően:

```bash
PEN_KEY_FILE="/scripts/init-premount/.penkey"           # a pendrive kotet
                                                # titkositasara hasznalt kulcs
PEN_DEV="/dev/disk/by-uuid/20b56d42-3184-4036-9e17-5ad2d07273ce" # pendrive
                                                                 # particio
PEN_NAME="pendrive"             # dm pendrive neve
PEN_MOUNT_POINT="/mnt/pendrive" # pendrive kotet felcsatolasanak a helye
SWAP_KEY_FILE="root.key"        # a swap titkositasanal hasznalt kulcs
SWAP_DEV="/dev/hda2"    # fizikai swap kotet
SWAP_NAME="swap"        # dm swap neve
```

## initrd frissítése

Nézzük meg milyen kernelt futtatunk:

```bash
uname -a
```

Linux moria `2.6.21.moria` #1 Sat May 5 12:11:17 CEST 2007 i686 GNU/Linux

Futtassuk az update-initramfs programot:

```bash
update-initramfs -v -u 2.6.21
```

Ellenőrizzük, ha LILO-t használunk, hogy a kernelünkhöz be van-e állítva az

```
initrd=/initrd.img
```

opció.

Futtassuk a lilo-t:

```bash
lilo
```

## Használat

A kernel bootolása előtt a pendrive-ot dugjuk be az usb csatlakozóba.

Az initrd futása alatt a rendszer észleli a pendrive-ot, kinyitja a pendrive titkosított kötetét, az ott talált kulcs alapján kinyitja a titkosított swap partíciót, majd megpróbálkozik a hibernált rendszer felélesztésével.

Ha nem talál hibernált adatokat, akkor folytatódik a rendszer normál betöltése.
