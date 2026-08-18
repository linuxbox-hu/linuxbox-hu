---
author: szimszon
categories:
- linux
created: 1216992132
date: '2008-07-25T00:00:00Z'
description: |
  A slashdot [http://linux.slashdot.org/linux/08/07/25/1150218.shtml cikke] nyomán (Foxconn alaplapra nem lehet linuxot telepíteni), találtam ezt az [http://howflow.com/tricks/medion_md_98300_fan_control oldalt].
  
  A lényeg, hogy kernel paraméternek meg lehet adni, hogy a linux mit hazudjon a BIOS ACPI-nek:
  
   acpi_os_name="Windows 2001 SP2" 
  
  Hogy ne csak vaktába lövöldözzünk kis fogodzkodó:
  
    strings /proc/acpi/dsdt | grep -i windows
title: Hogyan verjük át a BIOS ACPI-t...
aliases:
- /node/540/
- /story/540/
---
A slashdot [http://linux.slashdot.org/linux/08/07/25/1150218.shtml cikke] nyomán (Foxconn alaplapra nem lehet linuxot telepíteni), találtam ezt az [http://howflow.com/tricks/medion_md_98300_fan_control oldalt].

A lényeg, hogy kernel paraméternek meg lehet adni, hogy a linux mit hazudjon a BIOS ACPI-nek:

 acpi_os_name="Windows 2001 SP2" 

Hogy ne csak vaktába lövöldözzünk kis fogodzkodó:

  strings /proc/acpi/dsdt | grep -i windows
