---
excerpt: "Fel lehet fogni poénnak is, de azt is el tudom képzelni hogy valaki ragaszkodik
  aa megszokotott c:\\ -hez. :D\r\n<code>\r\nexport PS1='C:${PWD//\\//\\\\\\}>'\r\n</code>\r\nA
  kódsor lecseréli a $PWD változóban (aktuális elérési út) linuxos /-t windowsos \\-re
  így az eredmény: C:\\home\\ szerű prompt...\r\n\r\n<a href=\"http://agafix.org/april-foul-windows-like-bash-prompt/\">Eredeti
  cikk.</a>"
categories: []
layout: blog
author: kecsi
mail: kecsi@linuxbox.hu
title: Windows-os parancssori prompt linux alatt :)
created: 1230896181
---
Fel lehet fogni poénnak is, de azt is el tudom képzelni hogy valaki ragaszkodik aa megszokotott c:\ -hez. :D
<code>
export PS1='C:${PWD//\//\\\}>'
</code>
A kódsor lecseréli a $PWD változóban (aktuális elérési út) linuxos /-t windowsos \-re így az eredmény: C:\home\ szerű prompt...

<a href="http://agafix.org/april-foul-windows-like-bash-prompt/">Eredeti cikk.</a>
