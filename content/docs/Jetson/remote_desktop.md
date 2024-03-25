---
weight: 999
title: "Remote_desktop"
description: ""
icon: "article"
date: "2024-03-15T22:38:47-04:00"
lastmod: "2024-03-15T22:38:47-04:00"
draft: true
toc: true
---
misc links:
[jetson forms](https://forums.developer.nvidia.com/t/how-to-send-data-to-host-pc-using-micro-usb/154488/3)  
https://www.ubuntupit.com/how-to-install-and-use-xrdp-server-remote-desktop-on-linux-system/

When fully flashed the jetson acts a network and hosts on ip 192.168.55.100(on user)
and 192.168.55.1 on the jetson side.

after install xrdp on jetson run `sudo ufw allow 3389` to open the port
and add `sudo adduser xrdp ssl-cert`

## ssh via usb cable
you can automatically just ssh into the jetson via the usb-micro cable.
List the ports that were just connected `ls /dev/tty*` (in my case it was `/dev/ttyACM0`)
then run putty or minicom to connect to it.(in my case I used tio ` tio -b 115200 /dev/ttyUSB0`).
Then just login with username and password


## Installing rdp
{{< tabs tabTotal="4">}}
{{% tab tabName="Windows" %}}

Start > Settings  > System > Remote Desktop, and turn on Enable Remote Desktop.

In the search box type `Remote Desktop Connection` or `rdp`

{{% /tab %}}
{{% tab tabName="MacOS" %}}

TODO: 

{{% /tab %}}
{{% tab tabName="Linux" %}}

```bash
sudo apt-get install xrdp
systemctl start xrdp && systemctl enable xrdp
```


Note: It should automatically start itself and set itself to auto-start, but just in case, make sure it’s
running with sudo systemctl status xrdp

Typing `rdp` in the search bar works 99% of the time in Ubuntu.

Free KDE option is KRDC.

{{% /tab %}}
{{< /tabs >}}


Input your host username and the IP assigned to the USB interface (i.e. nvidia@192.168.55.1)
and connect. In my case, the USB interface is l4tbr0. No additional configuration is necessary
