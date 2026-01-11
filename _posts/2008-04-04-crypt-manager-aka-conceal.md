---
excerpt: "<a href=\"http://www.ubuntugeek.com/crypt-manager-an-encrypted-folder-manager-for-ubuntu-linux.html\">Ubuntugeek</a>
  -en akadtam a <a href=\"http://code.google.com/p/crypt-manager/\">Crypt manager</a>-re
  ami könyvtárak titkosításához ad grafikus felületet.\r\n\r\nA <a href=\"http://code.google.com/p/crypt-manager/downloads/list\">honlapon
  van bináris debian csomag letöltési</a> lehetőség de a svn verzió telepítése sem
  túl bonyolult (Ubuntura):\r\n"
categories:
- ubuntu
layout: story
author: kecsi
title: Crypt manager aka Conceal
created: 1207298630
---
<a href="http://www.ubuntugeek.com/crypt-manager-an-encrypted-folder-manager-for-ubuntu-linux.html">Ubuntugeek</a> -en akadtam a <a href="http://code.google.com/p/crypt-manager/">Crypt manager</a>-re ami könyvtárak titkosításához ad grafikus felületet.

A <a href="http://code.google.com/p/crypt-manager/downloads/list">honlapon van bináris debian csomag letöltési</a> lehetőség de a svn verzió telepítése sem túl bonyolult (Ubuntura):
<!--break--> 
<code>
sudo addgroup your-login fuse
sudo apt-get install encfs python2.4-dev python-nautilus subversion
svn checkout http://crypt-manager.googlecode.com/svn/trunk/ crypt-manager
cd crypt-manager
sudo ./install.sh
</code>
