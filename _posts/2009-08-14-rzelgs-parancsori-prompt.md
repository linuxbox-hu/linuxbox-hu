---
excerpt: "<a href=\"http://www.commandlinefu.com/commands/view/2528/smiley-face-bash-prompt\">Commandlinefu</a>-n
  találtam egy fópofa parancssori prompt beállítást. A prompt asszerint ha helyes
  utasítást adtál ki mosolyog (jó pofát vág) vagy ha hibás parancsot sikerült begépelned
  akkor furcsán vagy szomorúan néz rád. :D\r\nElső eredeti verzió:\r"
categories:
- linux
layout: story
author: kecsi
mail: kecsi@linuxbox.hu
title: Érzelgős parancsori prompt
created: 1250249750
---
<a href="http://www.commandlinefu.com/commands/view/2528/smiley-face-bash-prompt">Commandlinefu</a>-n találtam egy fópofa parancssori prompt beállítást. A prompt asszerint ha helyes utasítást adtál ki mosolyog (jó pofát vág) vagy ha hibás parancsot sikerült begépelned akkor furcsán vagy szomorúan néz rád. :D
Első eredeti verzió:
<code>export PS1="\`if [ \$? = 0 ]; then echo \e[33\;40m\\\^\\\_\\\^\e[0m; else echo \e[36\;40m\\\-\e[0m\\\_\e[36\;40m\\\-\e[0m; fi\` \u \w:\h)"</code>
egy kicsit módosított egy hozzászólásból
<code>export PS1="\`if [ \$? = 0 ]; then echo \[\e[34m\]^_^\[\e[0m\]; else echo \[\e[31m\]O_O\[\e[0m\]; fi\`[\u@\h:\w]\\$ "</code>
