---
excerpt: "Egyszerũ, gyors megoldás szín kiválasztásához.\r\n\r\n#!/bin/bash \r\nif
  [ -n \"$1\" ]; then\r\n        r=`printf %d 0x${1:0:2}`\r\n        g=`printf %d
  0x${1:2:2}`\r\n        b=`printf %d 0x${1:4:2}`\r\nfi\r\nprintf \"#%.2X%.2X%.2X\\n\"
  `Xdialog --stdout --colorsel color 20 55 $r $g $b`\r\n\r\n\r\n"
categories: []
layout: blog
author: bAndie91
mail: bandie9100@freemail.hu
title: color select
created: 1250635692
---
Egyszerũ, gyors megoldás szín kiválasztásához.

#!/bin/bash 
if [ -n "$1" ]; then
        r=`printf %d 0x${1:0:2}`
        g=`printf %d 0x${1:2:2}`
        b=`printf %d 0x${1:4:2}`
fi
printf "#%.2X%.2X%.2X\n" `Xdialog --stdout --colorsel color 20 55 $r $g $b`


