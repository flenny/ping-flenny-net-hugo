+++
comments = true
date = "2016-07-04T15:59:12+02:00"
description = "KB3148812 and KB3159706 causes WSUS to crash. Learn how to fix this problem."
draft = false
image = "images/post/default-post.png"
slug = "fix-wsus-unexpected-error-in-mmc-after-installing-windows-updates"
tags = ["wsus", "windows server"]
title = "Fix WSUS 'unexpected error' in MMC after installing Windows updates (KB3148812/KB3159706)"

+++

{{< figure src="/images/post/wsus-error.png" class="img-responsive center-block" alt="wsus error" >}}

**Update 4/7/2016: Same issue with KB3159706.**

After installing the latest Windows updates, WSUS Update Services MMC console gave me a nice 'Error: Unexpected Error' message. Removing and reconnecting the server in MMC, didn't help. Neither restarting 'WSUS Service' nor rebooting the server solved the problem. According to {{% a_blank "this" "http://blogs.technet.com/b/wsus/archive/2016/04/20/known-issues-with-kb3148812.aspx" %}} article Windows update KB3148812, which recently was released, broke Windows Server Update Services (WSUS). Uninstalling this specific update and rebooting the server fixed the problem.

{{< figure src="/images/post/wsus-remove-update.png" class="img-responsive center-block" alt="remove windows update" >}}