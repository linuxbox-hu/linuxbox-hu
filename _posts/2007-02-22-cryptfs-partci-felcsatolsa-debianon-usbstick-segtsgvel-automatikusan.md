---
excerpt: "<p>Az alap ötletet a <a set=\"yes\" href=\"http://www.debian-administration.org/articles/428\"
  class=\"external\" rel=\"nofollow\">http://www.debian-administration.org/articles/428</a>
  adta.\r\n</p>\r\n<p>Amit megvalósít:\r\n</p>\r\n<p>Debian Etch.\r\n</p>\r\n<p>Egy
  cryptfs-sel titkosított partíciót automatikusan, jelszó kérdezése nélkül, felcsatolni
  úgy, hogy a kulcs a pendrive-on van ((<b>b</b>)ami akár titkosítva is lehet a számítógépen
  tárolt kulcs segítségével(<b>/b</b>)).\r\n</p> "
categories:
- debian
layout: story
author: szimszon
title: Cryptfs partíció felcsatolása Debianon USBStick segítségével automatikusan
created: 1172155295
---
<p>Az alap ötletet a <a set="yes" href="http://www.debian-administration.org/articles/428" class="external" rel="nofollow">http://www.debian-administration.org/articles/428</a> adta.
</p>
<p>Amit megvalósít:
</p>
<p>Debian Etch.
</p>
<p>Egy cryptfs-sel titkosított partíciót automatikusan, jelszó kérdezése nélkül, felcsatolni úgy, hogy a kulcs a pendrive-on van ((<b>b</b>)ami akár titkosítva is lehet a számítógépen tárolt kulcs segítségével(<b>/b</b>)).
</p> <!--break-->
<h2><u><b>Előfeltételek</b></u>
</h2>
<p>A <b>cryptsetup</b> és <b>sharutils</b> csomagokra lesz szükség.
</p>
<p>Ellenőrizzük a <b>device mapper</b> működését:
</p>
<pre>root@test:~# ls -L /dev/mapper/control
/dev/mapper/control
</pre>
<p>és a titkosító kernel modulok működését:
</p>
<pre>root@test:~# cat /proc/crypto
[...]
name         &nbsp;: sha256
driver       &nbsp;: sha256-generic
module       &nbsp;: sha256
[...]
name         &nbsp;: aes
driver       &nbsp;: aes-i586
module       &nbsp;: aes_i586
[...]
</pre><a name="Amir.C5.91l_a_konkr.C3.A9t_p.C3.A9lda_sz.C3.B3l"></a>
<h2><u><b> Amiről a konkrét példa szól</b></u>
</h2> <dl><dt>A titkosítandó partíció</dt><dd> /dev/hda5 (/home)
<br />(<b>b</b>) /dev/sda1 (pendrive titkosított partíció)(<b>/b</b>) </dd><dt>A könyvtar ahova az adatokat elmentjük a <i>/home</i>-ból</dt><dd> /srv/home </dd><dt>A pendrive partíció neve (label)</dt><dd> secret
<br />(<b>b</b>) ha titkosítjuk a pendrive-ot, akkor <i>by-uuid</i>-et fogunk használni. (<b>/b</b>) </dd><dt>A pendrive partíció fájlrendszere</dt><dd> ext2 </dd><dt>A titkosításnál használt kulcs</dt><dd> root.key (és a <i>secret</i> kötet gyökerén található)
<br />(<b>b</b>)/etc/.penkey (a pendrive partíció titkosításánál használjuk fel) (<b>/b</b>)</dd></dl>
<p>Minden parancsot <i>root</i>-ként adjunk ki.
</p>
<p><b>Figyelem</b> adatvesztésért felelősséget nem vállalok! Mindenki járjon el kellő elővigyázatossággal!
</p><a name="A_part.C3.ADci.C3.B3_el.C5.91k.C3.A9sz.C3.ADt.C3.A9se"></a>
<h2><u><b> A partíció előkészítése</b></u>
</h2>
<p>Mentsünk le minden információt a partícióról:
</p>
<pre>cd /home
cp -arvx . /srv/home/
</pre>
<p>Csatoljuk le a <i>/home</i> partíciót:
</p>
<pre>umount /home
</pre>
<p>Majd minden információt tüntessünk el róla:
</p>
<pre>dd if=/dev/urandom of=/dev/hda5
</pre>
<h2><u><b> Pendrive előkészítése</b></u>
</h2>
<p><b>Figyelem</b> ennél a műveletnél a pendrive-on tárolt adatok elvesznek!
</p>
<p>Készítsünk egy ext2-es partíciót a pendrive-ra, ha a fat nem jó nekünk.
</p> cfdisk /dev/sda
<br />
<p>Formázzuk meg úgy az eszközt, hogy nevet (label) adunk a partíciónak.
</p>
<p>(<b>b</b>) Készítsünk egy kulcsot a pendrive-hoz is:&nbsp;
</p>
<pre>head -c 2880 /dev/urandom | uuencode -m - | head -n 65 | tail -n 64 &gt; /etc/.penkey
</pre>
<p>Ezután jöhet a partíció titkosítása:
</p>
<pre>cryptsetup -c aes-cbc-essiv:sha256 luksFormat /dev/sda1 /etc/.penkey
</pre>
<p>Nyissuk meg az eszközt:
</p>
<pre>cryptsetup --key-file /etc/.penkey luksOpen /dev/sda1 pendrive_secre</pre>
<p>(<b>/b</b>)
</p>
<p>fat
</p>
<pre></pre><dl><dd> mkfs.vfat -n "secret" /dev/sda1 </dd><dt>ext2</dt><dd> mkfs.ext2 -L "secret" /dev/sda1 </dd></dl>
<p>Jelen esetben:
</p>
<pre> mkfs.ext2 -L "secret" /dev/sda1
</pre>
<p>Ez ahhoz kell, hogy később egyszerűen tudja azonosítani az <b>udev</b> az eszközt.
</p>
<p>(<b>b</b>) ha a pendrive partíciót titkosítjuk akkor a label nem szükséges (<b>/b</b>)
</p>
<p>Csatoljuk fel a pendrive-ot, hogy a kulcsot már eleve oda generáljuk. (Atya tanácsára)
</p>
<pre> mount /dev/disk/by-label/secret /mnt/usb/pendrive
</pre>
<pre>(<b>b</b>)&nbsp; mount /dev/mapper/pendrive_secret /mnt/usb/pendrive(<b>/b</b>)</pre>
<h2><u><b>A partíció titkosítása</b></u>
</h2>
<p>Generáljuk le a kulcsot:
</p>
<pre>head -c 2880 /dev/urandom | uuencode -m - | head -n 65 | tail -n 64 &gt; /mnt/usb/pendrive/root.key
</pre>
<p>A fenti sor a <i>/mnt/usb/pendrive</i> könyvtár <b>root.key</b> fájljába véletlen karaktersorozatot generál, amit később kulcsként használunk.
</p>
<p>Ezután jöhet a partíció titkosítása:
</p>
<pre>cryptsetup -c aes-cbc-essiv:sha256 luksFormat /dev/hda5 /mnt/usb/pendrive/root.key</pre>
<p>Nyissuk meg az eszközt:
</p>
<pre>cryptsetup --key-file /mnt/usb/pendrive/root.key luksOpen /dev/hda5 home
</pre>
<p>Ezzel létrejön egy <i>/dev/mapper/home</i> kötet.
</p>
<p>Akár le is csatolhatjuk a pendrive-ot:
</p>
<pre>umount /mnt/usb/pendrive
<p>(<b>b</b>) Zárjuk le a pendrive titkosított partícióját:</p><pre>cryptsetup luksClose pendrive_secret
<p>(<b>/b</b>)&nbsp;</p></pre></pre>
<p>Most már megformázhatjuk az eszközt a kedvenc fájlrendszerünkre:
</p>
<pre>mkfs.ext3 /dev/mapper/home
</pre>
<p>Ezután fel lehet csatolni és visszamásolni az adatokat.
</p>
<pre>mount /dev/mapper/home /home
cd /srv/home
cp -axrv . /home


</pre><a name="Pendrive_el.C5.91k.C3.A9sz.C3.ADt.C3.A9se"></a>
<h2><u><b>UDEV tanítása</b></u>
</h2>
<p>Ehhez a <i>/etc/udev/rules.d/z20_persistent.rules</i> fájlt kell szerkeszteni:
</p>
<pre># UUID and volume label
KERNEL=="*[!0-9]", ATTR{removable}=="1", GOTO="no_volume_id"
IMPORT{program}="vol_id --export $tempnode"
ENV{ID_FS_UUID}=="?*",          ENV{ID_FS_USAGE}=="filesystem|other|crypto", \
       SYMLINK+="disk/by-uuid/$env{ID_FS_UUID}"
ENV{ID_FS_LABEL_SAFE}=="?*",    ENV{ID_FS_USAGE}=="filesystem|other", \
       SYMLINK+="disk/by-label/$env{ID_FS_LABEL_SAFE}"
</pre>
<p>sor után, ez a fájl vége felé van, közvetlenül írjuk be:
</p>
<pre>ENV{ID_FS_LABEL_SAFE}=="secret", ENV{ACTION}=="add", RUN+="/usr/local/sbin/cpmount"

(<b>b</b>)ENV{ID_FS_UUID}=="36AC-8D27", ENV{ACTION}=="add", RUN+="/usr/local/sbin/cpmount2"(<b>/b</b>)</pre>
<p>Ennek a sornak a lényege:
</p> <dl><dt>ENV{ID_FS_LABEL_SAFE}=="secret"</dt><dd> a program akkor fog lefutni, ha a partíció neve megegyezik <i>secret</i>-tel </dd><dt>ENV{ACTION}=="add"</dt><dd> és csak akkor ha éppen most lett csatlakoztatva a pendrive </dd><dt>RUN+="/usr/local/sbin/cpmount"</dt><dd> ha az előző két feltétel teljesül, akkor lefuttatja a <b>/usr/local/sbin/cpmount</b> scriptet.</dd>
<p>(<b>b</b>)
</p></dl><dl><dt>ENV{ID_FS_UUID}=="36AC-8D27"</dt><dd> a program akkor fog lefutni, ha a partíció <i>uuid</i>-je 36AC-8D27 (ezt a /dev/disk/by-uuid könyvtárban találjuk, meg kell nézni, hogy ha kihúzzuk a pendrive-ot, melyik uuid tűnik el:)</dd></dl><dl><dt>ENV{ACTION}=="add"</dt><dd> és csak akkor ha éppen most lett csatlakoztatva a pendrive </dd><dt>RUN+="/usr/local/sbin/cpmount2"</dt><dd> ha az előző két feltétel teljesül, akkor lefuttatja a <b>/usr/local/sbin/cpmount2</b> scriptet.</dd></dl><dl>
<p>(<b>/b</b>)&nbsp;
</p></dl><a name="cpmount_beszerz.C3.A9se"></a>
<h2><u><b> cpmount beszerzése</b></u>
</h2>
<p>Letölthető: <a href="http://linux.oregpreshaz.hu/cucc/cpmount/cpmount" class="external" title="http://linux.oregpreshaz.hu/cucc/cpmount/cpmount" rel="nofollow">cpmount</a><span class="urlexpansion">&nbsp;</span> <a href="http://linux.oregpreshaz.hu/cucc/cpmount/cpmount.asc" class="external" title="http://linux.oregpreshaz.hu/cucc/cpmount/cpmount.asc" rel="nofollow">.asc</a><span class="urlexpansion">&nbsp;</span>
</p>
<p>A script elején a
</p>
<pre>DEBUG=1                               # legyen-e loggolas
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
</pre>
<p>változókat kell átnézni, hogy megfelelnek-e a saját rendszerünk paramétereinek. <i>Minden javítást a scripthez szívesen fogadok!</i>
</p>
<p>Másoljuk a letöltött <b>cpmount</b> scriptet a <i>/usr/local/sbin</i> könyvtárba és ellenőrizzük, hogy rajta van-e a futtatási jogosultság.
</p>
<p>(<b>b</b>)
  <br />
</p>
<h2><u><b><u><b> cpmount2 beszerzése</b></u></b></u>
</h2>
<p>&nbsp;Letölthető: <a title="http://linux.oregpreshaz.eu/cucc/cpmount/cpmount2" target="_blank" href="http://linux.oregpreshaz.eu/cucc/cpmount/cpmount2">cpmount2</a>.<a title="http://linux.oregpreshaz.eu/cucc/cpmount/cpmount2.asc" target="_blank" href="http://linux.oregpreshaz.eu/cucc/cpmount/cpmount2.asc">asc</a>
</p>
<pre><a title="http://linux.oregpreshaz.eu/cucc/cpmount/cpmount2.asc" target="_blank" href="http://linux.oregpreshaz.eu/cucc/cpmount/cpmount2.asc"></a>DEBUG=1&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; # legyen-e loggolas
DISK="/dev/disk/by-uuid/36AC-8D27"&nbsp;&nbsp;&nbsp; # itt kell megadni, hogy mi a kulcsot
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; # tartalmazo disk particio neve (label)
FS_TYPE="ext2"&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; # a pendrive fajlrendszere
MOUNT="/mnt/usb/pendrive"&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; # ahova ideiglenesen fel lesz csatolva
KULCS="root.key"&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; # a kulcs neve, relativ a MOUNT-tol nezve
DEV="/dev/hda5"&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; # annak az eszkoznek a neve, ami
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; # titkositva lett
DEV_NAME="home"&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; # itt lehet megadni, hogy a cryptosetup
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; # milyen neven hozza letre a pszeudo-
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; # eszkozt
DEV_MOUNT="/home"&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; # vegso soron hova legyen felmountolva
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; # a titkositott particio
USB_WAIT=1&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; # ennyi masodpercet var amig megprobalja
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; # felcsatolni az usb eszkozt
PEN_KEY="/etc/.penkey"&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; # a pendrive-on levo particio dekodolasahoz
PEN_NAME="pendrive_kulcs"&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; # a pendrive particio $DIR_MAPPER neve
PRG_CRYPTSETUP="/sbin/cryptsetup"&nbsp;&nbsp;&nbsp;&nbsp; # cryptsetup program
PRG_MOUNT="/bin/mount"&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; # mount program
PRG_UMOUNT="/bin/umount"&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; # umount program
DIR_MAPPER="/dev/mapper"</pre>
<p> (<b>/b</b>)
</p><a name="A_mechanizmus_kipr.C3.B3b.C3.A1l.C3.A1sa"></a>
<h2><u><b> A mechanizmus kipróbálása</b></u>
</h2>
<p>Csatoljuk le a pendrive-ot, ha még nem tettük meg, és húzzuk ki.
</p>
<pre>umount /mnt/usb/pendrive
</pre>
<p>Csatoljuk le a <i>/home</i> -ot.
</p>
<pre>umount /home
</pre>
<p>Zárjuk be a titkosított eszközt:
</p>
<pre>cryptsetup luksClose /dev/mapper/home
</pre>
<p>Vegyünk egy mély levegőt és dugjuk vissza a pendrive-ot.
</p>
<p>Ha a script-ben a <i>DEBUG</i> változót <i>1</i>-re állítottuk, a syslog-ban megjelennek az üzenetek, amik megmutatják, hogy sikerült-e a <i>/home</i> felcsatolása vagy nem.
</p>
<p>A syslog-ban valami hasonlót kell látnunk:
</p>
<pre>mount_home: Megvan a pendrive...
mount_home: Pendrive felcsatolasa: [/dev/disk/by-label/secret] -&gt; [/mnt/usb/pendrive]
moria mount_home: Crypto device inicializalasa megtortent.
mount_home: [/home] felcsatolva
mount_home: [/mnt/usb/pendrive] lecsatolva
</pre>
<p>Ha itt hibát nem látunk, valószínűleg a <i>/home</i> kötetünk a helyére került, minden adatunkkal.&nbsp;:)
</p>
<p>Ha akarjuk a pendrive-ot eltávolíthatjuk.
</p>
<p>A dokumentum mindenkori aktuális verziója megtalálható a <a title="http://wiki.hup.hu/index.php/Cryptfs_part%C3%ADci%C3%B3_felcsatol%C3%A1sa_Debianon_USBStick_seg%C3%ADts%C3%A9g%C3%A9vel_automatikusan" target="_blank" href="http://wiki.hup.hu/index.php/Cryptfs_part%C3%ADci%C3%B3_felcsatol%C3%A1sa_Debianon_USBStick_seg%C3%ADts%C3%A9g%C3%A9vel_automatikusan">HupWiki</a>n.
  <br />
</p>
