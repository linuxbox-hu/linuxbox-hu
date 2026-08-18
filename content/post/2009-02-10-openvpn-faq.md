---
author: szimszon
categories: []
created: 1234259664
date: '2009-02-10T00:00:00Z'
description: 'http://www.ossg.ru/docs/OpenVPN/faq.html UDPv4 []: No buffer space available (code=105) Increase the required free memory. I recommend at least 2 MB, which you can set with: echo 2048 >/proc/sys/vm/min_free_kbytes'
title: openvpn faq
aliases:
- /blog/592/
- /node/592/
---
http://www.ossg.ru/docs/OpenVPN/faq.html

UDPv4 []: No buffer space available (code=105)

Increase the required free memory. I recommend at least 2 MB, which you can set with:

    echo 2048 >/proc/sys/vm/min_free_kbytes
