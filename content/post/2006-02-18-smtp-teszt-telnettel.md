---
author: kecsi
categories:
- linux
created: 1140259972
date: '2006-02-18T00:00:00Z'
description: 'SMTP szerver konfugurálás közben jól jön, ha telnettel tudunk mailszervert tesztelni. Íme egy példa: $ telnet smtp.pelda.hu smtp Trying 192.0.34.72... Connected to smtp.example.com. Escape character is ''^]''. 220 smtp.pelda.hu ESMTP Postfix (Debian/GNU) HELO smtp.vhol.hu 250 smtp.example.com MAIL From: kecsi@nemtomDEnemletezik.hu 250 Ok RCPT To: haver@valaholDEnemletezik.hu'
title: SMTP teszt telnettel
aliases:
- /node/128/
- /story/128/
---
SMTP szerver konfugurálás közben jól jön, ha telnettel tudunk mailszervert tesztelni.
Íme egy példa:
<code>
$ telnet smtp.pelda.hu smtp
Trying 192.0.34.72...
Connected to smtp.example.com.
Escape character is '^]'.
220 smtp.pelda.hu ESMTP Postfix (Debian/GNU)
HELO smtp.vhol.hu
250 smtp.example.com
MAIL From: kecsi@nemtomDEnemletezik.hu
250 Ok
RCPT To: haver@valaholDEnemletezik.hu
250 Ok
DATA
354 End data with <CR><LF>.<CR><LF>
Hello!
Kene nekem egykis linux segitseg.
.
250 Ok: queued as F169C23068
QUIT
221 Bye
Connection closed by foreign host. 
</code>
A levél végét a szöveg utolsó sorában a `.` adja!
