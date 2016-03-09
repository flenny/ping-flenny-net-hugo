+++
comments = true
date = "2016-03-09T21:05:00+01:00"
description = "Learn how to fix error 'index.php was not found on this server' after upgrading ownCloud to version 9."
draft = false
image = "images/post/logo/owncloud.png"
slug = "owncloud-9-fix-error-index-php-was-not-found"
tags = ["owncloud", "ubuntu"]
title = "Fix error 'index.php was not found on this server' after upgrading ownCloud to version 9"
+++

{{< figure src="/images/post/missing-index-php.png" class="img-responsive center-block" alt="ownCloud error message" >}}

If you just upgraded ownCloud on Ubuntu 15.10 to version 9 (using `apt-get dist-upgrade`),
you probably get the error message shown above. Adding `/index.php` manually still redirects to the ownCloud login screen. 

As mentioned [here](https://github.com/owncloud/core/issues/22970) open `.htaccess` in `/var/www/owncloud` an comment out
the line `RewriteRule .* index.php [PT,E=PATH_INFO:$1]`