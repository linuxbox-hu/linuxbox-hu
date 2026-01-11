---
excerpt: "A <a href=\"http://www.shell-fu.org/\">shell-fu</a> egy hasznos angol nyelvű
  shell szkript gyűjtemény. Jókat lehet benne böngészni. Ezt találtam pl:\r\n<a href=\"http://www.shell-fu.org/lister.php?id=313\">szkirpt
  a legfrisebb kernel letöltésére</a>\r\n<code>\r\n#!/bin/bash\r\nkernelV=`finger
  finger@kernel.org | grep 'stable version' | awk '{print $NF}'`\r\nwget -c http://www.kernel.org/pub/linux/kernel/v2.6/linux-$kernelV.tar.bz2\r\n</code>"
categories:
- linux
layout: story
author: kecsi
title: 'Shell-fu: szkirpt a legfrisebb kernel letöltésére'
created: 1224489553
---
A <a href="http://www.shell-fu.org/">shell-fu</a> egy hasznos angol nyelvű shell szkript gyűjtemény. Jókat lehet benne böngészni. Ezt találtam pl:
<a href="http://www.shell-fu.org/lister.php?id=313">szkirpt a legfrisebb kernel letöltésére</a>
<code>
#!/bin/bash
kernelV=`finger finger@kernel.org | grep 'stable version' | awk '{print $NF}'`
wget -c http://www.kernel.org/pub/linux/kernel/v2.6/linux-$kernelV.tar.bz2
</code>
