+++
date = "2016-01-21T18:04:43+01:00"
description = "Learn how to setup and update Proxmox Virtual Environment LXC container templates."
draft = false
tags = ["virtualization", "proxmox", "lxc"]
title = "How to update proxmox LXC container templates"
image = "images/post/default-post.png"
+++

{{< figure src="/images/post/logo/proxmox.png" class="img-responsive center-block" alt="Proxmox" >}}

By default LXC container templates are not available after installing Proxmox Virtual Environment. In order to enable templates for Ubuntu, Joomla, OwnCloud, WordRress or OpenVPN run the following command on your host's console.

    pveam update

You will find the templates right on your local storage > content > templates.

![lxc container templates](/images/post/pve-lxc-update.png)