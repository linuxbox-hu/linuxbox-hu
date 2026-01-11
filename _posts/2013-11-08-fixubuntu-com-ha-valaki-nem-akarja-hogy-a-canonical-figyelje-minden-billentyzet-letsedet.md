---
layout: post
title: fixubuntu.com - ha valaki nem akarja, hogy a Canonical figyelje minden billentyűzet leütésedet
  leütésedet
date: 2013-11-08
author: szimszon
categories: [linux]
tags:
 - Ubuntu
 - Spyware
---
Miután elolvastam az [Ars Technica](http://arstechnica.com/) [cikkét](http://arstechnica.com/information-technology/2013/11/canonical-abused-trademark-law-to-target-a-site-critical-of-ubuntu-privacy/) arról, hogy akarja a Canonical elhallgattatni a kritizáló oldalt, csak megnéztem miről is szól a [fixubuntu.com](https://fixubuntu.com/). Ezt találtam:

```gsettings set com.canonical.Unity.Lenses remote-content-search none; if [ "`/usr/bin/lsb_release -rs`" \< '13.10' ]; then sudo apt-get remove -y unity-lens-shopping; else gsettings set com.canonical.Unity.Lenses disabled-scopes "['more_suggestions-amazon.scope', 'more_suggestions-u1ms.scope', 'more_suggestions-populartracks.scope', 'music-musicstore.scope', 'more_suggestions-ebay.scope', 'more_suggestions-ubuntushop.scope', 'more_suggestions-skimlinks.scope']"; fi; echo | sudo tee -a /etc/hosts; echo 127.0.0.1 productsearch.ubuntu.com | sudo tee -a /etc/hosts;```

Javaslom mindenkinek, hogy először egy szövegszerkesztőbe (vim, gedit stb...) másolja a fenti szöveget, [sose lehet tudni... :)](http://thejh.net/misc/website-terminal-copy-paste)

Egyébként a fenti kód részlet tényleg nem csinál semmi különöset, csak kikapcsolja a Dash lencséit, amik az interneten keresnének a beírt kifejezésre. Bővebben [itt](https://fixubuntu.com/).

