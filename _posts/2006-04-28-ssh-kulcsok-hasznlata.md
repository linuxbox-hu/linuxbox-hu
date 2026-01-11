---
excerpt: "Ha egy távoli gépre például jelszó nélkül akarsz bejutni ssh-val, akkor
  használhatsz ssh kulcsokat.\r\nEnnek a beállítása mindössze pár utasítás:\r\n1.
  Generálj egy SSH kulcsot magadnak ehhez a művelethez.\r\n<code>ssh-keygen -t dsa</code>\r\nNe
  adj meg jelszót amikor jelszavas védelmet akar tenni a kulcsra.\r\n2. Másold át
  a publikus kulcsát a frissen generált kulcspárodnak(publikus és privát).\r\n<code>scp
  ~/.ssh/id_dsa.pub masikgep.teljes.neve:.ssh/authorized_keys2</code>\r\nEzután már
  próbálhasz is átlépnizni jelszó nélkül.\r\n<code>ssh masikgep.teljes.neve</code>"
categories:
- linux
layout: story
author: kecsi
title: SSH kulcsok használata
created: 1146247811
---
Ha egy távoli gépre például jelszó nélkül akarsz bejutni ssh-val, akkor használhatsz ssh kulcsokat.
Ennek a beállítása mindössze pár utasítás:
1. Generálj egy SSH kulcsot magadnak ehhez a művelethez.
<code>ssh-keygen -t dsa</code>
Ne adj meg jelszót amikor jelszavas védelmet akar tenni a kulcsra.
2. Másold át a publikus kulcsát a frissen generált kulcspárodnak(publikus és privát).
<code>scp ~/.ssh/id_dsa.pub masikgep.teljes.neve:.ssh/authorized_keys2</code>
Ezután már próbálhasz is átlépnizni jelszó nélkül.
<code>ssh masikgep.teljes.neve</code>
