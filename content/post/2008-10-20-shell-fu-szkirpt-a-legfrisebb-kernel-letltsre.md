---
author: kecsi
categories:
- linux
created: 1224489553
date: '2008-10-20T00:00:00Z'
description: 'A shell-fu egy hasznos angol nyelvű shell szkript gyűjtemény. Jókat lehet benne böngészni. Ezt találtam pl: szkirpt a legfrisebb kernel letöltésére #!/bin/bash kernelV=`finger finger@kernel.org | grep ''stable version'' | awk ''{print $NF}''` wget -c http://www.kernel.org/pub/linux/kernel/v2.6/linux-$kernelV.tar.bz2'
title: 'Shell-fu: szkirpt a legfrisebb kernel letöltésére'
aliases:
- /node/559/
- /story/559/
---
A <a href="http://www.shell-fu.org/">shell-fu</a> egy hasznos angol nyelvű shell szkript gyűjtemény. Jókat lehet benne böngészni. Ezt találtam pl:
<a href="http://www.shell-fu.org/lister.php?id=313">szkirpt a legfrisebb kernel letöltésére</a>
<code>
#!/bin/bash
kernelV=`finger finger@kernel.org | grep 'stable version' | awk '{print $NF}'`
wget -c http://www.kernel.org/pub/linux/kernel/v2.6/linux-$kernelV.tar.bz2
</code>
