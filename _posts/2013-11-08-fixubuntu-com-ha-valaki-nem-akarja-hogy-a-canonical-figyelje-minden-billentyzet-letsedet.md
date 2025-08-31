---
excerpt: <p>Miután elolvastam az <a title="http://arstechnica.com/" target="_blank"
  href="http://arstechnica.com/">Ars Technica</a> <a title="http://arstechnica.com/information-technology/2013/11/canonical-abused-trademark-law-to-target-a-site-critical-of-ubuntu-privacy/"
  target="_blank" href="http://arstechnica.com/information-technology/2013/11/canonical-abused-trademark-law-to-target-a-site-critical-of-
categories:
- ubuntu
layout: story
author: szimszon
mail: szimszon@oregpreshaz.eu
title: fixubuntu.com - ha valaki nem akarja, hogy a Canonical figyelje minden billentyűzet
  leütésedet
created: 1383943213
---
<p>Miután elolvastam az <a title="http://arstechnica.com/" target="_blank" href="http://arstechnica.com/">Ars Technica</a> <a title="http://arstechnica.com/information-technology/2013/11/canonical-abused-trademark-law-to-target-a-site-critical-of-ubuntu-privacy/" target="_blank" href="http://arstechnica.com/information-technology/2013/11/canonical-abused-trademark-law-to-target-a-site-critical-of-ubuntu-privacy/">cikkét</a> arról, hogy akarja a Canonical elhallgattatni a kritizáló oldalt, csak megnéztem miről is szól a <a title="https://fixubuntu.com/" target="_blank" href="https://fixubuntu.com/">fixubuntu.com</a>. Ezt találtam:
</p>
<hr /> <code>gsettings set com.canonical.Unity.Lenses remote-content-search none; if [ "`/usr/bin/lsb_release -rs`" \&lt; '13.10' ]; then sudo apt-get remove -y unity-lens-shopping; else gsettings set com.canonical.Unity.Lenses disabled-scopes "['more_suggestions-amazon.scope', 'more_suggestions-u1ms.scope', 'more_suggestions-populartracks.scope', 'music-musicstore.scope', 'more_suggestions-ebay.scope', 'more_suggestions-ubuntushop.scope', 'more_suggestions-skimlinks.scope']"; fi; echo | sudo tee -a /etc/hosts; echo 127.0.0.1 productsearch.ubuntu.com | sudo tee -a /etc/hosts;</code>
<hr />
<p> Javaslom mindenkinek, hogy először egy szövegszerkesztőbe (vim, gedit stb...) másolja a fenti szöveget, <a title="webről másolás veszélyei" target="_blank" href="http://thejh.net/misc/website-terminal-copy-paste">sose lehet tudni... :)</a>
</p>
<p>Egyébként a fenti kód részlet tényleg nem csinál semmi különöset, csak kikapcsolja a Dash lencséit, amik az interneten keresnének a beírt kifejezésre. Bővebben <a title="https://fixubuntu.com/" target="_blank" href="https://fixubuntu.com/">itt</a>.
  <br />
</p>
