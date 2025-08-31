---
excerpt: "Grrrr nagyon dühös vagyok a spammerekre. Utálom mikor idepiszkítanak a weboldalra.
  Már egy ideje captcha képek védik a regisztrációt. De visszatérnek a korábban beregisztrált
  falhasználóval és továbbra is szivatnak. Ma letöröltem gyanús felhsználók sokaságát
  első felindulásból.\r\nAki magyar domain névről, magyar felhasználó névvel regisztrált
  nem lehet veszélyben. Aki nagyon furcsa címről és furcsa felhasználó névvel regisztrált
  és nem volt soha aktív esetlegesen beleeshetett a szórásba. Sajnálom. Regisztráljon
  újra.\r\n"
categories: []
layout: blog
author: kecsi
mail: kecsi@linuxbox.hu
title: spammerek
created: 1190102750
---
Grrrr nagyon dühös vagyok a spammerekre. Utálom mikor idepiszkítanak a weboldalra. Már egy ideje captcha képek védik a regisztrációt. De visszatérnek a korábban beregisztrált falhasználóval és továbbra is szivatnak. Ma letöröltem gyanús felhsználók sokaságát első felindulásból.
Aki magyar domain névről, magyar felhasználó névvel regisztrált nem lehet veszélyben. Aki nagyon furcsa címről és furcsa felhasználó névvel regisztrált és nem volt soha aktív esetlegesen beleeshetett a szórásba. Sajnálom. Regisztráljon újra.
<!--break-->
Itt látszik, hogy már 110 felhasználót töröltem a múltban...
<code>
drupal5=> select count(*) from users;
 count
-------
   632
(1 sor)

drupal5=> select max(uid) from users;
 max
-----
 742
(1 sor)
</code>
