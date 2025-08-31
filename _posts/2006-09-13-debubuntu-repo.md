---
excerpt: "Beleakadtam a <a href=\"http://repository.debuntu.org/\">debuntu</a> Dapper
  Drake és Edgy Eft deb csomag repozitorijába.\r\nDapperre pl igy vehetjük fel:\r\n<code>\r\ndeb
  http://repository.debuntu.org/ dapper multiverse\r\ndeb-src http://repository.debuntu.org/
  dapper multiverse\r\n</code>\r\nmajd\r\n<code>\r\nwget http://repository.debuntu.org/GPG-Key-chantra.txt\r\nsudo
  apt-key add GPG-Key-chantra.txt\r\nrm GPG-Key-chantra.txt\r\n</code>\r\ntelepíthetünk
  innét: gaim 2.0.0beta3.1, audacious és subtitleeditor csomagokat."
categories:
- ubuntu
layout: story
author: kecsi
mail: kecsi@linuxbox.hu
title: debubuntu repo
created: 1158141565
---
Beleakadtam a <a href="http://repository.debuntu.org/">debuntu</a> Dapper Drake és Edgy Eft deb csomag repozitorijába.
Dapperre pl igy vehetjük fel:
<code>
deb http://repository.debuntu.org/ dapper multiverse
deb-src http://repository.debuntu.org/ dapper multiverse
</code>
majd
<code>
wget http://repository.debuntu.org/GPG-Key-chantra.txt
sudo apt-key add GPG-Key-chantra.txt
rm GPG-Key-chantra.txt
</code>
telepíthetünk innét: gaim 2.0.0beta3.1, audacious és subtitleeditor csomagokat.
