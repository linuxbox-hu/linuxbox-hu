---
author: kecsi
categories:
- linux
created: 1115062852
date: '2005-05-02T00:00:00Z'
excerpt: 'A httpd.conf-ba a köv két sort tegyük be: ServerSignature Off ServerTokens Prod A netcraft elõtte: ·Apache/1.3.XX (Unix) Debian GNU/Linux PHP/4.X.X· ennyi infot nyert a web szerverrõl. Utána: ·Apache'
title: Apache verziószám és egyéb infó elrejtés
aliases:
- /node/64/
- /story/64/
---
A httpd.conf-ba a köv két sort tegyük be:
```text
ServerSignature Off
ServerTokens Prod
```
A netcraft elõtte: ·Apache/1.3.XX (Unix) Debian GNU/Linux PHP/4.X.X· ennyi infot nyert a web szerverrõl. Utána: ·Apache
