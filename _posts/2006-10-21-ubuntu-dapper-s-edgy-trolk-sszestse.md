---
excerpt: "#------------------------------------------------------------------------------\r\n#
  Bonfire avagy Brasero ubuntu alá, CD-író progi\r\n# GPG kulcs az apt-getnek\r\n#
  <code>wget -q http://mrpouit.tuxfamily.org/12B83718.gpg -O- | sudo apt-key add -</code>\r\n\r\n#
  deb http://mrpouit.tuxfamily.org dapper-pouit contrib\r\n# deb-src http://mrpouit.tuxfamily.org
  dapper-pouit contrib\r\n\r\n<code>deb http://mrpouit.tuxfamily.org edgy-pouit extra</code>\r\n<code>deb-src
  http://mrpouit.tuxfamily.org edgy-pouit extra</code>\r\n#------------------------------------------------------------------------------\r\n#
  Beleakadtam a debuntu Dapper Drake és Edgy Eft deb csomag repozitorijába.\r"
categories: []
layout: blog
author: vaskalap
title: Ubuntu dapper és edgy tárolók összesítése
created: 1161421220
---
#------------------------------------------------------------------------------
# Bonfire avagy Brasero ubuntu alá, CD-író progi
# GPG kulcs az apt-getnek
# <code>wget -q http://mrpouit.tuxfamily.org/12B83718.gpg -O- | sudo apt-key add -</code>

# deb http://mrpouit.tuxfamily.org dapper-pouit contrib
# deb-src http://mrpouit.tuxfamily.org dapper-pouit contrib

<code>deb http://mrpouit.tuxfamily.org edgy-pouit extra</code>
<code>deb-src http://mrpouit.tuxfamily.org edgy-pouit extra</code>
#------------------------------------------------------------------------------
# Beleakadtam a debuntu Dapper Drake és Edgy Eft deb csomag repozitorijába.
# <code>wget http://repository.debuntu.org/GPG-Key-chantra.txt</code>
# <code>sudo apt-key add GPG-Key-chantra.txt</code>
# <code>rm GPG-Key-chantra.txt</code>
# telepíthetünk innét: gaim 2.0.0betaX.X, audacious és subtitleeditor csomagokat
# Dapperre pl igy vehetjük fel:

<code>deb http://repository.debuntu.org/ edgy multiverse</code>
<code>deb-src http://repository.debuntu.org/ edgy multiverse</code>

# deb http://repository.debuntu.org/ dapper multiverse
# deb-src http://repository.debuntu.org/ dapper multiverse
#------------------------------------------------------------------------------
<code>deb http://hu.archive.ubuntu.com/ubuntu/ edgy main restricted universe multiverse</code>
<code>deb http://hu.archive.ubuntu.com/ubuntu/ edgy-updates main restricted universe multiverse</code>
<code>deb http://hu.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse</code>
<code>deb http://hu.archive.ubuntu.com/ubuntu/ edgy-security main restricted universe multiverse</code>
<code>deb http://hu.archive.ubuntu.com/ubuntu/ edgy-proposed main restricted universe multiverse</code>
<code>deb http://packages.freecontrib.org/ubuntu/plf/ edgy-plf free non-free</code>

#deb http://hu.archive.ubuntu.com/ubuntu/ dapper main restricted
#deb-src http://hu.archive.ubuntu.com/ubuntu/ dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
#deb http://hu.archive.ubuntu.com/ubuntu/ dapper-updates main restricted
#deb-src http://hu.archive.ubuntu.com/ubuntu/ dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb http://hu.archive.ubuntu.com/ubuntu/ dapper universe
# deb-src http://hu.archive.ubuntu.com/ubuntu/ dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://hu.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
# deb-src http://hu.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

#deb http://security.ubuntu.com/ubuntu dapper-security main restricted
#deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
# deb http://security.ubuntu.com/ubuntu dapper-security universe
# deb-src http://security.ubuntu.com/ubuntu dapper-security universe

