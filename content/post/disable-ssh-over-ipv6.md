+++
comments = true
date = "2016-01-31T22:31:43+01:00"
description = "How to disable SSH over IPv6."
draft = false
image = "images/post/default-post.png"
tags = ["ssh", "ipv6", "ubuntu"]
title = "Disable SSH connections over IPv6"
+++

If a network interface offers IPv4 as well as IPv6, by default ubuntu's SSH server listens on both IP versions. In order to restrict access to protocol version 4 you have to comment in the line `#ListenAddress 0.0.0.0` in your `/etc/ssh/sshd_config`.

~~~vim
#ListenAddress ::
ListenAddress 0.0.0.0
~~~

Restart SSH service for the changes to take effect.

~~~bash
sudo service sshd restart
~~~