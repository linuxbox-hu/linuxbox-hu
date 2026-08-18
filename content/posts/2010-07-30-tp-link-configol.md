---
author: bAndie91
categories: []
created: 1280524317
date: '2010-07-30T00:00:00Z'
excerpt: 'Mivel lecseréltem a SOHO routeremet, http://linuxbox.hu/node/664 testvéreként
  írtam TP-LINK konfigoló szkriptet. Ezt tudja, igyekszem bõvíteni:'
title: tp-link configoló
aliases:
- /blog/670/
- /node/670/
---
Mivel lecseréltem a SOHO routeremet, <http://linuxbox.hu/node/664> testvéreként írtam TP-LINK konfigoló szkriptet. Ezt tudja, igyekszem bõvíteni:
<!--break-->
```
tl-wr543g.sh: [command] [-u user] [--] [host]
  command    one of these:
     dhclients    list hosts that requested DHCP address
     hosts        generate /etc/hosts file
     survey       list of available access points
     reserv       DHCP address reservation
     log          system log
     reboot       reboot device software
     stat         trafic statistics
     version      version information about device
     backup       save all configuration settings
  user       username for basic http authenticate
  host       ip or dns address of TL-WR543G device
```
