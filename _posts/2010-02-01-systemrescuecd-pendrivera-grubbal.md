---
excerpt: "Ha valahol át kell méretezni valamilyen partíciót, hálózatot kell tesztelni,
  vagy akár nagy tömegben kell klónozni partíciót/diszket jól jön a linuxos <a href=\"http://www.sysresccd.org/Main_Page\">SystemRescueCd</a>.
  Évek óta nagy megelégedéssel használom ezt a kitűnő live disztribúciót, amely ~250MB
  méretéhez képest hihetetlen sok alkalmazást tartalmaz. Természetesen nem csak CD-ről
  futtatható, jól érzi magát egy pendriveon is. Alap boot managere a syslinux, ami
  egyszerű és nagyszerű, de ha valakinek a menüs Grub hiányzik, hát íme a recept lépésről-lépésre.\r\n"
categories:
- linux
layout: story
author: Goosfrabaa
mail: gabrea@freemail.hu
title: SystemRescueCd pendrivera grubbal
created: 1265063553
---
Ha valahol át kell méretezni valamilyen partíciót, hálózatot kell tesztelni, vagy akár nagy tömegben kell klónozni partíciót/diszket jól jön a linuxos <a href="http://www.sysresccd.org/Main_Page">SystemRescueCd</a>. Évek óta nagy megelégedéssel használom ezt a kitűnő live disztribúciót, amely ~250MB méretéhez képest hihetetlen sok alkalmazást tartalmaz. Természetesen nem csak CD-ről futtatható, jól érzi magát egy pendriveon is. Alap boot managere a syslinux, ami egyszerű és nagyszerű, de ha valakinek a menüs Grub hiányzik, hát íme a recept lépésről-lépésre.
<!--break-->
<strong>Először is egy USB-ről futó változatot kell készíteni.</strong>
(Ha a hivatalos módon (a systemrescuecd.iso felcsatolása és az usb_inst.sh futtatása után) "No Default or UI found" hibaüzenetet kapunk, akkor érdemes a pen driveot FAT16-ra formattálni -egyes régi BIOSokon állítólag csak ezzel a trükkel indul.
Ha ez sem segít, akkor a <a href=" http://rufus.akeo.ie/?locale=hu_HU">rufus</a> nevű Windowsos progit ajánlom, amivel könnyedén lehet bootolható USB eszközöket készíteni.)


Az eredeti leírás (nagyrészt) <a href=" http://www.sysresccd.org/Sysresccd-manual-en_How_to_install_SystemRescueCd_on_an_USB-stick#Installation_from_Linux">itt</a> található. (Figyelem ez a leírás Linux alóli megoldásról szól és végig root nevében dolgozunk):
<ul>
<li>Töltsük le az aktuális iso imaget (mondjuk a <strong>/tmp/</strong> alá)!
Pl: <em>wget http://kent.dl.sourceforge.net/project/systemrescuecd/sysresccd-x86/1.3.5/systemrescuecd-x86-1.3.5.iso -P /tmp/</em></li>
<li>Csatlakoztassunk egy pendriveot és figyeljük meg, hogyan látja a rendszerünk!
Pl: <em>fdisk -l</em>
<cite><strong>/dev/sdb1</strong>   *           1         121      971901    c  W95 FAT32 (LBA)</cite>
</li>
<li>Formattáljuk a pendrive partícióját (Figyelem! Minden adat elvész!)
Pl: <em>mkfs.vfat -F 32 -n SYSRESC /dev/sdb1</em></li>
<li>A pendrive MBR-ba kerül a syslinux (nálam a syslinux a /usr/lib/syslinux könyvtárban található)
Pl: <em>dd if=/usr/lib/syslinux/mbr.bin of=/dev/sdb</em>
Egy szinkronizálás nem árt, hogy biztosan minden az eszközre kerüljön
<em>sync</em></li>
<li>Mountoljuk fel a pendriveot (ha nincs <strong>/mnt/usbstick/</strong> könyvtár, akkor azt először létre kell hozni)!
Pl:
<em>mkdir /mnt/usbstick
mount -t vfat /dev/sdb1 /mnt/usbstick</em></li>
<li>Mountoljuk fel az iso fájl tartalmát (ha nincs <strong>/mnt/cdrom/</strong> könyvtár, akkor azt először létre kell hozni)!
Pl:
<em>mkdir /mnt/cdrom
mount /tmp/systemrescuecd-x86-1.3.5.iso /mnt/cdrom -o loop</em></li>
<li>Másoljuk a fájlokat a CD-ről a pendrivera!
Pl:
<em>cp -af /mnt/cdrom/* /mnt/usbstick/
rm -rf /mnt/usbstick/syslinux
mv /mnt/usbstick/isolinux/isolinux.cfg /mnt/usbstick/isolinux/syslinux.cfg
mv /mnt/usbstick/isolinux /mnt/usbstick/syslinux</em></li>
<li>Lecsatoljuk a pendriveot és bootolhatóvá tesszük
Pl:
<em>umount /mnt/usbstick/
syslinux /dev/sdb1
sync</em></li>
<li>A CD image-et is lecsatoljuk, már nincs rá szükség
Pl: <em>umount /mnt/cdrom/</em></li>
<strong>Ezzel egy syslinuxos SystemRescueCd-t kaptunk pendriveon, amivel már be lehetne bootolni.
Változtassuk meg a boot managert Grubra...</strong>
<li>Mountoljuk fel a pendriveot!
Pl: <em>mount -t vfat /dev/sdb1 /mnt/usbstick</em></li>
<li>Hozzuk létre a grub könyvtárat!
Pl: <em>mkdir -p /mnt/usbstick/boot/grub</em></li>
<li>Másoljuk fel a pendrive megfelelő könyvtárába a grub fájljait (igazából nem kell mind, de elférnek..).
Nálam ezek a /usr/lib/grub/i386-pc/ könyvtárban találhatók:
Pl: <em>cp /usr/lib/grub/i386-pc/* /mnt/usbstick/boot/grub</em></li>

<li>Készítsünk egy <strong>menu.lst</strong> fájlt a Grubnak:
Pl: <em>cat > /mnt/usbstick/boot/grub/menu.lst
# Alapertekek:
timeout   5
default   0
color light-blue/black light-cyan/blue

# (0) System Rescue CD
title SystemRescueCd 32bit
kernel (hd0,0)/syslinux/rescuecd setkmap=us docache lowmem
initrd (hd0,0)/syslinux/initram.igz</em>[ctrl-d]

<li>Válasszuk le a a pendriveot!
Pl: <em>umount /mnt/usbstick</em></li>

További menüket (szokásosan felmountolt pendrive esetén) a <strong>/mnt/usbstick/syslinux/syslinux.cfg</strong> fájl tanulmányozásával készíthetünk.</li>
<li>Bootoljunk be a pendriveról (BIOS-ban USB-HDD) és installáljuk a Grubot az MBR-be a syslinux helyére!
(Miután bebootolt pendriveról a rendszer -feltételezve, hogy merevlemezünk a hd0, pendrive pedig hd1):
<em>grub
root (hd1,0)
setup (hd1)
quit</em>
</li>
</ul>

<strong>Kész</strong> (de én is mire bepötyögtem)...
