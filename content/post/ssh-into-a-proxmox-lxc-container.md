+++
date = "2016-01-26T16:46:46+01:00"
description = "Learn how to SSH into a Proxmox LXC container."
draft = false
image = "images/post/default-post.png"
slug = "ssh-into-a-proxmox-lxc-container"
tags = ["proxmox", "lxc", "virtualization"]
title = "SSH into a Proxmox LXC container"
comments = true
+++

{{< figure src="/images/post/logo/proxmox.png" class="img-responsive center-block" alt="Proxmox" >}}

By default it's not possible to establish a direct SSH connection to a Proxmox LXC container. In order to SSH into a container there are two options available. Either you attach to the container through Proxmox host or you allow login with password on the specific container.

## Option #1: Attach to the container through Proxmox host  ##

Login to your Proxmox host and attach to the container with the following command.

~~~bash
lxc-attach --name 109
~~~

The name of the container corresponds to the unique VM ID which you can see in the container's description.

![ssh into a container](/images/post/ssh-into-container-001.png)

![ssh into a container](/images/post/ssh-into-container.png)

## Option #2: Allow login with password on the specific container  ##

By default a Proxmox LXC container allows root login only with public key authentication. To login to a container with username/password login to your Proxmox host and attach to the container with the following command.

~~~bash
lxc-attach --name 109
~~~

Open `sshd_config`

~~~bash
nano /etc/ssh/sshd_config
~~~

and change the line `PermitRootLogin without-password` to `PermitRootLogin yes`. Exit nano with `Ctrl+X` and save changes with `y` and `ENTER`.

![ssh into a container](/images/post/ssh-into-container-002.png)

Restart ssh service for the changes to take effect.

~~~bash
service ssh restart
~~~

Try to establish a direct SSH connection to your container's IP (If you don't know the container's IP run `ifconfig`).