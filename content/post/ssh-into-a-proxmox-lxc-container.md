+++
date = "2016-01-26T16:46:46+01:00"
description = "Learn how to ssh into a proxmox lxc container."
draft = false
image = "images/post/default-post.png"
tags = ["proxmox", "lxc", "virtualization"]
title = "SSH into a proxmox lxc container"
comments = true
+++

By default it's not possible to establish a direct ssh connection to a proxmox lxc container. In order to ssh into a container there are two options available. Either you attach to the container through proxmox host or you allow login with password on the specific container.

## Option #1: Attach to the container through proxmox host  ##

Login to your proxmox host and attach to the container with the following command.

    lxc-attach --name 109

The name of the container corresponds to the unique VM ID which you can see in the container's description.

![ssh into a container](/images/post/ssh-into-container-001.png)

![ssh into a container](/images/post/ssh-into-container.png)

## Option #2: Allow login with password on the specific container  ##

By default a proxmox lxc container allows root login only with public key authentication. To login to a container with username/password login to your proxmox host and attach to the container with the following command.

    lxc-attach --name 109

Open `sshd_config`

    nano /etc/ssh/sshd_config

and change the line `PermitRootLogin without-password` to `PermitRootLogin yes`. Exit nano with `Ctrl+X` and save changes with `y` and `ENTER`.

![ssh into a container](/images/post/ssh-into-container-002.png)

Restart ssh service for the changes to take effect.

    service ssh restart