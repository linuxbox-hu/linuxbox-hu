---
excerpt: "<strong>perl -e \"print crypt('jelszó', join '', ('.', '/', 0..9, 'A'..'Z',
  'a'..'z')[rand 64, rand 64]);\"</strong>\r\nÉrtelemszerűen cseréld le a \"jelszó\"
  szöveget az általad kriptálni kívánt jelszóra!"
categories:
- linux
layout: story
author: kecsi
title: Perl crypt egysoros
created: 1107210788
---
<strong>perl -e "print crypt('jelszó', join '', ('.', '/', 0..9, 'A'..'Z', 'a'..'z')[rand 64, rand 64]);"</strong>
Értelemszerűen cseréld le a "jelszó" szöveget az általad kriptálni kívánt jelszóra!
