---
author: Goosfrabaa
categories:
- linux
created: 1265063553
date: '2010-02-01T00:00:00Z'
description: 'Ha valahol át kell méretezni valamilyen partíciót, hálózatot kell tesztelni,
  vagy akár nagy tömegben kell klónozni partíciót/diszket jól jön a linuxos SystemRescueCd.'
title: SystemRescueCd pendrivera grubbal
aliases:
- /node/657/
- /story/657/
---
Ha valahol át kell méretezni valamilyen partíciót, hálózatot kell tesztelni, vagy akár nagy tömegben kell klónozni partíciót/diszket jól jön a linuxos [SystemRescueCd](http://www.sysresccd.org/Main_Page). Évek óta nagy megelégedéssel használom ezt a kitűnő live disztribúciót, amely ~250MB méretéhez képest hihetetlen sok alkalmazást tartalmaz. Természetesen nem csak CD-ről futtatható, jól érzi magát egy pendriveon is. Alap boot managere a syslinux, ami egyszerű és nagyszerű, de ha valakinek a menüs Grub hiányzik, hát íme a recept lépésről-lépésre.
<!--break-->
`Először is egy USB-ről futó változatot kell készíteni.`
(Ha a hivatalos módon (a systemrescuecd.iso felcsatolása és az usb_inst.sh futtatása után) "No Default or UI found" hibaüzenetet kapunk, akkor érdemes a pen driveot FAT16-ra formattálni -egyes régi BIOSokon állítólag csak ezzel a trükkel indul.
Ha ez sem segít, akkor a [rufus](http://rufus.akeo.ie/?locale=hu_HU) nevű Windowsos progit ajánlom, amivel könnyedén lehet bootolható USB eszközöket készíteni.)

Az eredeti leírás (nagyrészt) [itt](http://www.sysresccd.org/Sysresccd-manual-en_How_to_install_SystemRescueCd_on_an_USB-stick#Installation_from_Linux) található. (Figyelem ez a leírás Linux alóli megoldásról szól és végig root nevében dolgozunk):

1. Töltsük le az aktuális iso imaget (mondjuk a `/tmp/` alá)!
   Pl: `wget http://kent.dl.sourceforge.net/project/systemrescuecd/sysresccd-x86/1.3.5/systemrescuecd-x86-1.3.5.iso -P /tmp/`
2. Csatlakoztassunk egy pendriveot és figyeljük meg, hogyan látja a rendszerünk!
   Pl: `fdisk -l`
   `/dev/sdb1`   *           1         121      971901    c  W95 FAT32 (LBA)
3. Formattáljuk a pendrive partícióját (Figyelem! Minden adat elvész!)
   Pl: `mkfs.vfat -F 32 -n SYSRESC /dev/sdb1`
4. A pendrive MBR-ba kerül a syslinux (nálam a syslinux a /usr/lib/syslinux könyvtárban található)
   Pl: `dd if=/usr/lib/syslinux/mbr.bin of=/dev/sdb`
   Egy szinkronizálás nem árt, hogy biztosan minden az eszközre kerüljön
   `sync`
5. Mountoljuk fel a pendriveot (ha nincs `/mnt/usbstick/` könyvtár, akkor azt először létre kell hozni)!
   Pl:
   ```bash
   mkdir /mnt/usbstick
   mount -t vfat /dev/sdb1 /mnt/usbstick
   ```
6. Mountoljuk fel az iso fájl tartalmát (ha nincs `/mnt/cdrom/` könyvtár, akkor azt először létre kell hozni)!
   Pl:
   ```bash
   mkdir /mnt/cdrom
   mount /tmp/systemrescuecd-x86-1.3.5.iso /mnt/cdrom -o loop
   ```
7. Másoljuk a fájlokat a CD-ről a pendrivera!
   Pl:
   ```bash
   cp -af /mnt/cdrom/* /mnt/usbstick/
   rm -rf /mnt/usbstick/syslinux
   mv /mnt/usbstick/isolinux/isolinux.cfg /mnt/usbstick/isolinux/syslinux.cfg
   mv /mnt/usbstick/isolinux /mnt/usbstick/syslinux
   ```
8. Lecsatoljuk a pendriveot és bootolhatóvá tesszük
   Pl:
   ```bash
   umount /mnt/usbstick/
   syslinux /dev/sdb1
   sync
   ```
9. A CD image-et is lecsatoljuk, már nincs rá szükség
   Pl: `umount /mnt/cdrom/`

**Ezzel egy syslinuxos SystemRescueCd-t kaptunk pendriveon, amivel már be lehetne bootolni. Változtassuk meg a boot managert Grubra...**

10. Mountoljuk fel a pendriveot!
    Pl: `mount -t vfat /dev/sdb1 /mnt/usbstick`
11. Hozzuk létre a grub könyvtárat!
    Pl: `mkdir -p /mnt/usbstick/boot/grub`
12. Másoljuk fel a pendrive megfelelő könyvtárába a grub fájljait (igazából nem kell mind, de elférnek..).
    Nálam ezek a /usr/lib/grub/i386-pc/ könyvtárban találhatók:
    Pl: `cp /usr/lib/grub/i386-pc/* /mnt/usbstick/boot/grub`
13. Készítsünk egy `menu.lst` fájlt a Grubnak:
    Pl:
    ```text
    cat > /mnt/usbstick/boot/grub/menu.lst
    # Alapertekek:
    timeout   5
    default   0
    color light-blue/black light-cyan/blue

    # (0) System Rescue CD
    title SystemRescueCd 32bit
    kernel (hd0,0)/syslinux/rescuecd setkmap=us docache lowmem
    initrd (hd0,0)/syslinux/initram.igz
    ```
    majd `[ctrl-d]`
14. Válasszuk le a a pendriveot!
    Pl: `umount /mnt/usbstick`

    További menüket (szokásosan felmountolt pendrive esetén) a `/mnt/usbstick/syslinux/syslinux.cfg` fájl tanulmányozásával készíthetünk.
15. Bootoljunk be a pendriveról (BIOS-ban USB-HDD) és installáljuk a Grubot az MBR-be a syslinux helyére!
    (Miután bebootolt pendriveról a rendszer -feltételezve, hogy merevlemezünk a hd0, pendrive pedig hd1):
    ```bash
    grub
    root (hd1,0)
    setup (hd1)
    quit
    ```

**Kész** (de én is mire bepötyögtem)...
