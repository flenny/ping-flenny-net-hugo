+++
comments = true
date = "2016-02-18T14:04:50+01:00"
description = "Learn how to redirect HTTP to HTTP in ISS."
draft = false
image = "images/post/default-post.png"
slug = "http-to-https-with-url-rewrite-module-in-iis"
tags = ["iis", "ssl"]
title = "Redirect HTTP to HTTPS with URL rewrite module in IIS"
+++

{{< figure src="/images/post/logo/iis.png" class="img-responsive center-block" alt="IIS 9" >}}

First download [Microsoft's Web Platform Installer 5.0](http://go.microsoft.com/fwlink/?LinkId=255386).
It's a free tool that makes getting the latest components for Internet Information Services (IIS) easy. In Web Platform Installer search for 'url rewrite' and and install the one and only search result 'URL Rewrite 2.0'. Restart IIS in order to make URL Rewrite module visible as shown below.

{{< figure src="/images/post/iis-rewrite-module.png" class="img-responsive center-block" alt="IIS URL Rewrite module" >}}

Create a new blank rule with the following adjustments (leave default values):

- **Title**: e.g. 'Redirect to HTTPS'
- **Match URL**: Request URL matches the pattern using regular expressions. Pattern: `(.*)`
- **Conditions**: Add new. Condition input `{HTTPS}`, pattern `^OFF$`
- **Action**: Action type Redirect, Redirect URL `https://{HTTP_HOST}/{R:1}` redirect type 303

Apply and go back to rules overview.

{{< figure src="/images/post/iis-rewrite-module-001.png" class="img-responsive center-block" alt="IIS URL Rewrite module" >}}

**Don't forget to clear 'Require SSL' checkbox in SSL settings in order to make the redirect working properly.**