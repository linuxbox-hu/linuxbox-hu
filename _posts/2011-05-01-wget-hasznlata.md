---
excerpt: "Néha jó lenne egy weboldal tartalmát figyelni és a változásokról értesülni.
  Azonban az önaláírt ssl tanúsítvány, a http authentikáció, vagy épp az alkalmazásban
  megírt authentikációs form akadályozza ezt.\r\n"
categories: []
layout: blog
author: siposg
mail: rg@linuxscripting.hu
title: wget használata
created: 1304275076
---
Néha jó lenne egy weboldal tartalmát figyelni és a változásokról értesülni. Azonban az önaláírt ssl tanúsítvány, a http authentikáció, vagy épp az alkalmazásban megírt authentikációs form akadályozza ezt.
<!--break-->
Először nézzünk egy egyszerű index.html letöltést:
<code>wget -q http://tesztoldalam.hu</code>
Erre kapunk egy lementett index.html oldalt szerencsés esetben. Ha az oldal önaláírt tanúsítvánnyal titkosított kapcsolatot fogad csak el, akkor tanúsítvány hiba miatt nem jutunk hozzá az oldalhoz. Hogyan lehet ezt megkerülni?
<code>wget -q --no-check-certificate https://tesztoldalam.hu</code>

Akit részletesebben érdekel a téma megtekintheti bővebben <a href="http://linuxscripting.hu/?q=node/136#comment-138">itt.</a>
