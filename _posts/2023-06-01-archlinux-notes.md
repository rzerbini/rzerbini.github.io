---
title: ArchLinux Notes
date: 2023-06-01 00:00 -500
categories: [home, linux]
tags: [arch, servo, etc]                              # Tag always lowercase
---

## ArchLinux Notes

------------------------------
* ### ArchlinuxInstall *

use systemctl restart systemd-networkd

editar /etc/systemd/network/20-wired.network incluir

[Network]

DNS=8.8.8.8

DNS=8.8.4.4

DNS=1.1.1.1

add to /etc/resolv.conf the nameserver=8.8.8.8

-------
* 1
* 2
* 3

```bash
sudo pacman -Syyu && sudo pacman -U package.tar.gz hight light 
```

## tmp increase
```
mount -o remount,size=5G /tmp/
```

## XFCE$ Keyboard shortcuts
```
~/.config/xfce4/xfconf/xfce-perchannel-xml/xfce4-keyboard-shortcuts.xml\
~/.config/Thunar/accels.scm\
~/.config/xfce4/terminal/accels.scm`\
```