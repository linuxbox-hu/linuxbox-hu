---
excerpt: "Ha készült wget leírás, nem hagyhatom ki a másik jó kis grabbert: a curl-t.\r\n"
categories: []
layout: blog
author: siposg
mail: rg@linuxscripting.hu
title: curl használata
created: 1304783024
---
Ha készült wget leírás, nem hagyhatom ki a másik jó kis grabbert: a curl-t.
<!--break-->
Először nézzünk egy egyszerű index.html letöltést:
curl http://tesztoldalam.hu

Az eredményt a képernyőn kapjuk meg, eltérően a wget-től, ahol alapértelmezetten fájlba kerül.
Önaláírt tanúsítványok megkerülése:
curl -k https://tesztoldalam.hu vagy
curl --insecure https://tesztoldalam.hu

Bővebben a témáról itt <a href="http://linuxscripting.hu/?q=node/137">itt</a>  lehet olvasni.
