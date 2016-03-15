+++
comments = true
date = "2016-01-21T18:04:43+01:00"
description = "Learn how to setup and update Proxmox Virtual Environment LXC container templates."
draft = false
slug = "how-to-update-proxmox-lxc-container-templates"
tags = ["virtualization", "proxmox", "lxc"]
title = "How to update Proxmox LXC container templates"
image = "images/post/default-post.png"
+++

{{< figure src="/images/post/logo/proxmox.png" class="img-responsive center-block" alt="Proxmox" >}}

By default LXC container templates are not available after installing Proxmox Virtual Environment (PVE).
In order to enable templates for Ubuntu, Joomla, OwnCloud, WordRress or OpenVPN run the following command
on your host's console.

~~~bash
pveam update
~~~

You will find the templates right on your local storage > content > templates.

{{< figure src="/images/post/pve-lxc-update.png" class="img-responsive center-block" alt="LXC container templates" >}}