---
author: szimszon
categories:
- debian
created: 1172155295
date: '2007-02-22T00:00:00Z'
excerpt: 'Egy cryptfs-sel titkosított partíciót automatikusan, jelszó kérdezése nélkül,
  felcsatolni úgy, hogy a kulcs a pendrive-on van.'
title: Cryptfs partíció felcsatolása Debianon USBStick segítségével automatikusan
aliases:
- /node/314/
- /story/314/
---
Az alap ötletet a <http://www.debian-administration.org/articles/428> adta.

Amit megvalósít:

Debian Etch.

Egy cryptfs-sel titkosított partíciót automatikusan, jelszó kérdezése nélkül, felcsatolni úgy, hogy a kulcs a pendrive-on van (ami akár titkosítva is lehet a számítógépen tárolt kulcs segítségével).

## Előfeltételek

A `cryptsetup` és `sharutils` csomagokra lesz szükség.

Ellenőrizzük a `device mapper` működését:

```bash
root@test:~# ls -L /dev/mapper/control
/dev/mapper/control
```

és a titkosító kernel modulok működését:

```bash
root@test:~# cat /proc/crypto
[...]
name         : sha256
driver       : sha256-generic
module       : sha256
[...]
name         : aes
driver       : aes-i586
module       : aes_i586
[...]
```

## Amiről a konkrét példa szól

- **A titkosítandó partíció**: /dev/hda5 (/home) (vagy /dev/sda1, a pendrive titkosított partíciója)
- **A könyvtar ahova az adatokat elmentjük a `/home`-ból**: /srv/home
- **A pendrive partíció neve (label)**: secret (ha titkosítjuk a pendrive-ot, akkor `by-uuid`-et fogunk használni)
- **A pendrive partíció fájlrendszere**: ext2
- **A titkosításnál használt kulcs**: root.key (és a `secret` kötet gyökerén található), vagy /etc/.penkey (a pendrive partíció titkosításánál használjuk fel)

Minden parancsot `root`-ként adjunk ki.

**Figyelem** adatvesztésért felelősséget nem vállalok! Mindenki járjon el kellő elővigyázatossággal!

## A partíció előkészítése

Mentsünk le minden információt a partícióról:

```bash
cd /home
cp -arvx . /srv/home/
```

Csatoljuk le a `/home` partíciót:

```bash
umount /home
```

Majd minden információt tüntessünk el róla:

```bash
dd if=/dev/urandom of=/dev/hda5
```

## Pendrive előkészítése

**Figyelem** ennél a műveletnél a pendrive-on tárolt adatok elvesznek!

Készítsünk egy ext2-es partíciót a pendrive-ra, ha a fat nem jó nekünk.

```bash
cfdisk /dev/sda
```

Formázzuk meg úgy az eszközt, hogy nevet (label) adunk a partíciónak.

Ha a pendrive-ot is titkosítani szeretnénk, készítsünk egy kulcsot a pendrive-hoz is:

```bash
head -c 2880 /dev/urandom | uuencode -m - | head -n 65 | tail -n 64 > /etc/.penkey
```

Ezután jöhet a partíció titkosítása:

```bash
cryptsetup -c aes-cbc-essiv:sha256 luksFormat /dev/sda1 /etc/.penkey
```

Nyissuk meg az eszközt:

```bash
cryptsetup --key-file /etc/.penkey luksOpen /dev/sda1 pendrive_secre
```

Ezután a fájlrendszert kell létrehozni: `fat` esetén `mkfs.vfat -n "secret" /dev/sda1`, `ext2` esetén `mkfs.ext2 -L "secret" /dev/sda1`.

Jelen esetben:

```bash
mkfs.ext2 -L "secret" /dev/sda1
```

Ez ahhoz kell, hogy később egyszerűen tudja azonosítani az `udev` az eszközt. (Ha a pendrive partíciót titkosítjuk akkor a label nem szükséges.)

Csatoljuk fel a pendrive-ot, hogy a kulcsot már eleve oda generáljuk. (Atya tanácsára)

```bash
mount /dev/disk/by-label/secret /mnt/usb/pendrive
```

Ha a pendrive-ot titkosítottuk:

```bash
mount /dev/mapper/pendrive_secret /mnt/usb/pendrive
```

## A partíció titkosítása

Generáljuk le a kulcsot:

```bash
head -c 2880 /dev/urandom | uuencode -m - | head -n 65 | tail -n 64 > /mnt/usb/pendrive/root.key
```

A fenti sor a `/mnt/usb/pendrive` könyvtár `root.key` fájljába véletlen karaktersorozatot generál, amit később kulcsként használunk.

Ezután jöhet a partíció titkosítása:

```bash
cryptsetup -c aes-cbc-essiv:sha256 luksFormat /dev/hda5 /mnt/usb/pendrive/root.key
```

Nyissuk meg az eszközt:

```bash
cryptsetup --key-file /mnt/usb/pendrive/root.key luksOpen /dev/hda5 home
```

Ezzel létrejön egy `/dev/mapper/home` kötet.

Akár le is csatolhatjuk a pendrive-ot:

```bash
umount /mnt/usb/pendrive
```

Ha a pendrive-ot titkosítottuk, zárjuk le a pendrive titkosított partícióját:

```bash
cryptsetup luksClose pendrive_secret
```

Most már megformázhatjuk az eszközt a kedvenc fájlrendszerünkre:

```bash
mkfs.ext3 /dev/mapper/home
```

Ezután fel lehet csatolni és visszamásolni az adatokat.

```bash
mount /dev/mapper/home /home
cd /srv/home
cp -axrv . /home
```

## UDEV tanítása

Ehhez a `/etc/udev/rules.d/z20_persistent.rules` fájlt kell szerkeszteni:

```bash
# UUID and volume label
KERNEL=="*[!0-9]", ATTR{removable}=="1", GOTO="no_volume_id"
IMPORT{program}="vol_id --export $tempnode"
ENV{ID_FS_UUID}=="?*",          ENV{ID_FS_USAGE}=="filesystem|other|crypto", \
       SYMLINK+="disk/by-uuid/$env{ID_FS_UUID}"
ENV{ID_FS_LABEL_SAFE}=="?*",    ENV{ID_FS_USAGE}=="filesystem|other", \
       SYMLINK+="disk/by-label/$env{ID_FS_LABEL_SAFE}"
```

sor után, ez a fájl vége felé van, közvetlenül írjuk be:

```bash
ENV{ID_FS_LABEL_SAFE}=="secret", ENV{ACTION}=="add", RUN+="/usr/local/sbin/cpmount"
```

Ha a pendrive-ot titkosítottuk (uuid alapján):

```bash
ENV{ID_FS_UUID}=="36AC-8D27", ENV{ACTION}=="add", RUN+="/usr/local/sbin/cpmount2"
```

Ennek a sornak a lényege:

- `ENV{ID_FS_LABEL_SAFE}=="secret"`: a program akkor fog lefutni, ha a partíció neve megegyezik `secret`-tel
- `ENV{ACTION}=="add"`: és csak akkor ha éppen most lett csatlakoztatva a pendrive
- `RUN+="/usr/local/sbin/cpmount"`: ha az előző két feltétel teljesül, akkor lefuttatja a `/usr/local/sbin/cpmount` scriptet.

A titkosított pendrive változatnál hasonlóan:

- `ENV{ID_FS_UUID}=="36AC-8D27"`: a program akkor fog lefutni, ha a partíció `uuid`-je 36AC-8D27 (ezt a /dev/disk/by-uuid könyvtárban találjuk, meg kell nézni, hogy ha kihúzzuk a pendrive-ot, melyik uuid tűnik el)
- `ENV{ACTION}=="add"`: és csak akkor ha éppen most lett csatlakoztatva a pendrive
- `RUN+="/usr/local/sbin/cpmount2"`: ha az előző két feltétel teljesül, akkor lefuttatja a `/usr/local/sbin/cpmount2` scriptet.

## cpmount beszerzése

Letölthető: [cpmount](http://linux.oregpreshaz.hu/cucc/cpmount/cpmount) [.asc](http://linux.oregpreshaz.hu/cucc/cpmount/cpmount.asc)

A script elején a

```bash
DEBUG=1                               # legyen-e loggolas
DISK="/dev/disk/by-label/secret"      # itt kell megadni, hogy mi a kulcsot
                                      # tartalmazo disk particio neve (label)
FS_TYPE="ext2"                        # a pendrive fajlrendszere
MOUNT="/mnt/usb/pendrive"             # ahova ideiglenesen fel lesz csatolva
KULCS="root.key"                      # a kulcs neve, relativ a MOUNT-tol nezve
DEV="/dev/hda5"                       # annak az eszkoznek a neve, ami
                                      # titkositva lett
DEV_NAME="home"                       # itt lehet megadni, hogy a cryptosetup
                                      # milyen neven hozza letre a pszeudo-
                                      # eszkozt
DEV_MOUNT="/home"                     # vegso soron hova legyen felmountolva
                                      # a titkositott particio
USB_WAIT=1                            # ennyi masodpercet var amig megprobalja
                                      # felcsatolni az usb eszkozt
```

változókat kell átnézni, hogy megfelelnek-e a saját rendszerünk paramétereinek. *Minden javítást a scripthez szívesen fogadok!*

Másoljuk a letöltött `cpmount` scriptet a `/usr/local/sbin` könyvtárba és ellenőrizzük, hogy rajta van-e a futtatási jogosultság.

## cpmount2 beszerzése

Letölthető: [cpmount2](http://linux.oregpreshaz.eu/cucc/cpmount/cpmount2).[asc](http://linux.oregpreshaz.eu/cucc/cpmount/cpmount2.asc)

```bash
DEBUG=1                               # legyen-e loggolas
DISK="/dev/disk/by-uuid/36AC-8D27"    # itt kell megadni, hogy mi a kulcsot
                                      # tartalmazo disk particio neve (label)
FS_TYPE="ext2"                        # a pendrive fajlrendszere
MOUNT="/mnt/usb/pendrive"             # ahova ideiglenesen fel lesz csatolva
KULCS="root.key"                      # a kulcs neve, relativ a MOUNT-tol nezve
DEV="/dev/hda5"                       # annak az eszkoznek a neve, ami
                                      # titkositva lett
DEV_NAME="home"                       # itt lehet megadni, hogy a cryptosetup
                                      # milyen neven hozza letre a pszeudo-
                                      # eszkozt
DEV_MOUNT="/home"                     # vegso soron hova legyen felmountolva
                                      # a titkositott particio
USB_WAIT=1                            # ennyi masodpercet var amig megprobalja
                                      # felcsatolni az usb eszkozt
PEN_KEY="/etc/.penkey"                # a pendrive-on levo particio dekodolasahoz
PEN_NAME="pendrive_kulcs"             # a pendrive particio $DIR_MAPPER neve
PRG_CRYPTSETUP="/sbin/cryptsetup"     # cryptsetup program
PRG_MOUNT="/bin/mount"                # mount program
PRG_UMOUNT="/bin/umount"              # umount program
DIR_MAPPER="/dev/mapper"
```

## A mechanizmus kipróbálása

Csatoljuk le a pendrive-ot, ha még nem tettük meg, és húzzuk ki.

```bash
umount /mnt/usb/pendrive
```

Csatoljuk le a `/home`-ot.

```bash
umount /home
```

Zárjuk be a titkosított eszközt:

```bash
cryptsetup luksClose /dev/mapper/home
```

Vegyünk egy mély levegőt és dugjuk vissza a pendrive-ot.

Ha a script-ben a `DEBUG` változót `1`-re állítottuk, a syslog-ban megjelennek az üzenetek, amik megmutatják, hogy sikerült-e a `/home` felcsatolása vagy nem.

A syslog-ban valami hasonlót kell látnunk:

```
mount_home: Megvan a pendrive...
mount_home: Pendrive felcsatolasa: [/dev/disk/by-label/secret] -> [/mnt/usb/pendrive]
moria mount_home: Crypto device inicializalasa megtortent.
mount_home: [/home] felcsatolva
mount_home: [/mnt/usb/pendrive] lecsatolva
```

Ha itt hibát nem látunk, valószínűleg a `/home` kötetünk a helyére került, minden adatunkkal. :)

Ha akarjuk a pendrive-ot eltávolíthatjuk.

A dokumentum mindenkori aktuális verziója megtalálható a [HupWiki](http://wiki.hup.hu/index.php/Cryptfs_part%C3%ADci%C3%B3_felcsatol%C3%A1sa_Debianon_USBStick_seg%C3%ADts%C3%A9g%C3%A9vel_automatikusan)n.
