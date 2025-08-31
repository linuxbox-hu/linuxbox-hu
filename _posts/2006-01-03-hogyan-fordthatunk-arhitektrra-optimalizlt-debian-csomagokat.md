---
excerpt: "Az <b>apt-build</b> debian csomag segítségével gentoo stílusú architektúrára
  optimalizált debian csomagokat készíthetünk magunknak.\r\nTelepítsük fel először
  a csomagot.\r\n<pre>\r\n  $ wajig install apt-build\r\n</pre>\r\nközben kérdez bennünk
  pár opcióról, ezek a <em>/etc/apt/apt-build.conf</em> állományba kerülnek lementésre:\r\n<code>\r\n
  \ build-dir = /var/cache/apt-build/build\r\n  repository-dir = /var/cache/apt-build/repository\r\n
  \ Olevel = -O2\r\n  march = -march=pentium4\r\n  mcpu = -mcpu=pentium4\r\n  options
  = \" \"\r\n</code>\r"
categories:
- debian
layout: story
author: kecsi
mail: kecsi@linuxbox.hu
title: Hogyan fordíthatunk arhitektúrára optimalizált debian csomagokat.
created: 1136325221
---
Az <b>apt-build</b> debian csomag segítségével gentoo stílusú architektúrára optimalizált debian csomagokat készíthetünk magunknak.
Telepítsük fel először a csomagot.
<pre>
  $ wajig install apt-build
</pre>
közben kérdez bennünk pár opcióról, ezek a <em>/etc/apt/apt-build.conf</em> állományba kerülnek lementésre:
<code>
  build-dir = /var/cache/apt-build/build
  repository-dir = /var/cache/apt-build/repository
  Olevel = -O2
  march = -march=pentium4
  mcpu = -mcpu=pentium4
  options = " "
</code>
Az elkészült csomagok a <em>/var/cache/apt-build/repository</em> könyvtárba kerülnek. Innét aztán egyszerűen telepíthetjük is őket, ha beadjuk a következő sort a <em>/etc/apt/sources.list</em> konfigurációs állományunk elejére. (apt-build telepítése közben automatikusan is megtehettük ezt.)
<code>deb file:/var/cache/apt-build/repository apt-build main</code>

Továbbá természetesen meg kell adnunk a források elérhetőségét is ugyanitt!

Ha ez is megvan neki is láthatunk csomagokat fordítani miután frissítettük a csomag informacióink!

<code>  $ sudo apt-build install most</code>

Amennyiben elkészítjük a /etc/apt/apt-build.list állományt az újrafordítandó csomagok listájával akkor ezeket a csomagokat egyszerre mind is fordíthatjuk.

Például ebből az állományból is kiindulhatunk:
<code>
  # dpkg --get-selections | awk '{if ($2 == "install") print $1}' \
    > /etc/apt/apt-build.list
</code>
Ne felejtsük kivenni a gcc és hasonló a művelet elvégzéséhez szükséges csomagot kivenni a listánkból! Ezután már csak:
<code>
  $ sudo apt-build world
</code>
