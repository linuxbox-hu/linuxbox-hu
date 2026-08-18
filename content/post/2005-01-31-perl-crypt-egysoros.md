---
author: kecsi
categories:
- linux
created: 1107210788
date: '2005-01-31T00:00:00Z'
description: perl -e "print crypt('jelszó', join '', ('.', '/', 0..9, 'A'..'Z', 'a'..'z')[rand 64, rand 64]);" Értelemszerűen cseréld le a "jelszó" szöveget az általad kriptálni kívánt jelszóra!
title: Perl crypt egysoros
aliases:
- /node/1/
- /story/1/
---
`perl -e "print crypt('jelszó', join '', ('.', '/', 0..9, 'A'..'Z', 'a'..'z')[rand 64, rand 64]);"`
Értelemszerűen cseréld le a "jelszó" szöveget az általad kriptálni kívánt jelszóra!
