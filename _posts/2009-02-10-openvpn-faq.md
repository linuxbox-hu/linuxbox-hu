---
excerpt: "http://www.ossg.ru/docs/OpenVPN/faq.html\r\n\r\nUDPv4 []: No buffer space
  available (code=105)\r\n\r\nIncrease the required free memory. I recommend at least
  2 MB, which you can set with:\r\n\r\n    echo 2048 >/proc/sys/vm/min_free_kbytes"
categories: []
layout: blog
author: szimszon
title: openvpn faq
created: 1234259664
---
http://www.ossg.ru/docs/OpenVPN/faq.html

UDPv4 []: No buffer space available (code=105)

Increase the required free memory. I recommend at least 2 MB, which you can set with:

    echo 2048 >/proc/sys/vm/min_free_kbytes
