---
excerpt: "A slashdot [http://linux.slashdot.org/linux/08/07/25/1150218.shtml cikke]
  nyomán (Foxconn alaplapra nem lehet linuxot telepíteni), találtam ezt az [http://howflow.com/tricks/medion_md_98300_fan_control
  oldalt].\r\n\r\nA lényeg, hogy kernel paraméternek meg lehet adni, hogy a linux
  mit hazudjon a BIOS ACPI-nek:\r\n\r\n acpi_os_name=\"Windows 2001 SP2\" \r\n\r\nHogy
  ne csak vaktába lövöldözzünk kis fogodzkodó:\r\n\r\n  strings /proc/acpi/dsdt |
  grep -i windows\r\n"
categories:
- linux
layout: story
author: szimszon
mail: szimszon@oregpreshaz.eu
title: Hogyan verjük át a BIOS ACPI-t...
created: 1216992132
---
A slashdot [http://linux.slashdot.org/linux/08/07/25/1150218.shtml cikke] nyomán (Foxconn alaplapra nem lehet linuxot telepíteni), találtam ezt az [http://howflow.com/tricks/medion_md_98300_fan_control oldalt].

A lényeg, hogy kernel paraméternek meg lehet adni, hogy a linux mit hazudjon a BIOS ACPI-nek:

 acpi_os_name="Windows 2001 SP2" 

Hogy ne csak vaktába lövöldözzünk kis fogodzkodó:

  strings /proc/acpi/dsdt | grep -i windows
