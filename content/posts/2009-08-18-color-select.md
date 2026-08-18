---
author: bAndie91
categories: []
created: 1250635692
date: '2009-08-18T00:00:00Z'
excerpt: 'Egyszerũ, gyors megoldás szín kiválasztásához. #!/bin/bash if [ -n "$1" ]; then r=`printf %d 0x${1:0:2}` g=`printf %d 0x${1:2:2}` b=`printf %d 0x${1:4:2}` fi printf "#%.2X%.2X%.2X " `Xdialog --stdout --colorsel color 20 55 $r $g $b`'
title: color select
aliases:
- /blog/633/
- /node/633/
---
Egyszerũ, gyors megoldás szín kiválasztásához.

#!/bin/bash 
if [ -n "$1" ]; then
        r=`printf %d 0x${1:0:2}`
        g=`printf %d 0x${1:2:2}`
        b=`printf %d 0x${1:4:2}`
fi
printf "#%.2X%.2X%.2X\n" `Xdialog --stdout --colorsel color 20 55 $r $g $b`


