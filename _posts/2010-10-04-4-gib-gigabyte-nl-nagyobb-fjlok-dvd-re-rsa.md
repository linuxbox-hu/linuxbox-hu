---
excerpt: "Amennyiben 4 GiB-nál nagyobb (pl az asztali DVD recorder által készített
  4,3 GiB-os) fájlt akarunk DVD-re írni, az ISO9660 fájlrendszer helyett célszerűbb
  UDF-et választani.\r\n"
categories:
- linux
layout: story
author: Goosfrabaa
title: 4 GiB (Gigabyte)-nál nagyobb fájlok DVD-re írása
created: 1286217072
---
Amennyiben 4 GiB-nál nagyobb (pl az asztali DVD recorder által készített 4,3 GiB-os) fájlt akarunk DVD-re írni, az ISO9660 fájlrendszer helyett célszerűbb UDF-et választani.
<!--break-->
UDF esetében nem gond a 2GiB-nál nagyobb fájlméret (az "UDF White Paper" szerint max. 128 terabyte lehet). Én a következő parancsokat használom DVD írásra:
<code><em>
# Az írásra szánt fájlok helye:
Dir="/tmp/kiirando_fajlok_konyvtara/"
# DVD-RW lemez törlése (DVD+RW esetén törlés nélkül lehet írni):
wodim -v dev=/dev/dvdrw blank=fast
# mehet az írás:
growisofs -dvd-compat -allow-limited-size -udf -Z /dev/dvdrw -r -J $Dir</em></code>
