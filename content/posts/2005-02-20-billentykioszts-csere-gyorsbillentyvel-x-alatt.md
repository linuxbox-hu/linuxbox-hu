---
author: kecsi
categories:
- x
created: 1108918091
date: '2005-02-20T00:00:00Z'
excerpt: |
  Sajnos debian woody és sarge alatt sem működik rendesen az XFree86 szerver több billentyűkiosztás konfigurálása.
  Ezért manuálisan kellett a billenyűzet kiosztást cserélnem, mindaddig míg rá nem jöttem:
  <strong>setxkbmap -rules xfree86 -model logicordless -layout "us,hu"  -option "grp:alt_shift_toggle"</strong> paranccsal be lehet konfigurálni a gyorsbillentyűt paranccssorb=l! Mig az XFconfig-ba hiába írtam be az ezzel azonos sorokat. :(
title: billentyűkiosztás csere gyorsbillentyűvel X alatt
---
Sajnos debian woody és sarge alatt sem működik rendesen az XFree86 szerver több billentyűkiosztás konfigurálása.
Ezért manuálisan kellett a billenyűzet kiosztást cserélnem, mindaddig míg rá nem jöttem:
<strong>setxkbmap -rules xfree86 -model logicordless -layout "us,hu"  -option "grp:alt_shift_toggle"</strong> paranccsal be lehet konfigurálni a gyorsbillentyűt paranccssorb=l! Mig az XFconfig-ba hiába írtam be az ezzel azonos sorokat. :(
<!--break-->
<code>
Ami ez így néz ki:
Section "InputDevice"
        Identifier  "Keyboard0"
        Driver      "keyboard"
        Option      "XkbRules" "xfree86"
        Option      "XkbModel" "pc105"
        Option      "XkbLayout" "us,hu"
        Option      "XkbVariant" ","
        Option      "XkbOptions" "grp:ctrl_shift_toggle"
        #Option "XkbCompat" "group_led"
        #Option "XkbOptions" "grp:switch,grp:alt_shift_toggle,grp_led:scroll" 
EndSection
</code>
