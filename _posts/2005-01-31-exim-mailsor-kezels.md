---
excerpt: "Aktualis mailsor: \r\n&nbsp;<strong>mailq</strong>\r\nLevél kivétele a sorbol:\r\n&nbsp;<strong>exim
  -Mrm 175TfP-0004uA-00 17CTav-0007R5-00</strong>\r\nA reject/retry azaz kézbesíthetetlen
  címek adatbázisának törlése:\r\n&nbsp;<strong>exim_tidydb -t 0d /var/spool/exim/
  reject</strong>\r\n&nbsp;<strong>exim_tidydb -t 0d /var/spool/exim/ retry</strong>\r\nMailq
  újrafeldolgozás: \r\n&nbsp;<strong>exim -qf</strong>\r\n&nbsp;<strong>exim -qff</strong>\r\n"
categories:
- linux
layout: story
author: kecsi
mail: kecsi@linuxbox.hu
title: exim mailsor kezelés
created: 1107211302
---
Aktualis mailsor: 
&nbsp;<strong>mailq</strong>
Levél kivétele a sorbol:
&nbsp;<strong>exim -Mrm 175TfP-0004uA-00 17CTav-0007R5-00</strong>
A reject/retry azaz kézbesíthetetlen címek adatbázisának törlése:
&nbsp;<strong>exim_tidydb -t 0d /var/spool/exim/ reject</strong>
&nbsp;<strong>exim_tidydb -t 0d /var/spool/exim/ retry</strong>
Mailq újrafeldolgozás: 
&nbsp;<strong>exim -qf</strong>
&nbsp;<strong>exim -qff</strong>
