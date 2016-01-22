+++
date = "2016-01-21T18:04:43+01:00"
description = "abstract"
draft = false
tags = ["virtualization", "proxmox", "lxc"]
title = "How to update proxmox lxc container templates"

+++

By default lxc container templates are not available after installing Proxmox Virtual Environment. In order to enable templates for Ubuntu, Joomla, OwnCloud, WordRress or OpenVPN run the following command on your hosts console.

    pveam update

You will find the templates right on your local storage > content > templates.

![lxc container templates](/images/post/pve-lxc-update.png)