---
title: "Resolving Ubuntu Failure with Suspend Mode"
date: 2025-01-03
featured: true
description: "I have experienced issues where Ubuntu automatically _wakes up_ from sleep mode almost instantly after
being put into `suspend`. 
This blog post describes what caused the issue and how I fixed it."
tags: ["Ubuntu"]
image: ""
fact: ""
weight: 500
sitemap:
  priority : 0.8
---

A few weeks after receiving my new work laptop, running Ubuntu 24.04, I  noticed that the battery would often be very 
low or dead when I left it in _suspend_ mode. 
Although this wasn't a major issue, it was rather inconvenient, so I decided to investigate further and see if I could
get this working properly.
This blog post describes what caused the issue and how I fixed it.

#### Symptom 
When you put the laptop into _suspend_ mode, it immediately 'wakes up' again.
It then stays 'awake', waiting for user input, and slowly draining the battery.
I experienced this issue with Ubuntu 24.04.

#### Problem
The issue seems to be caused by a “Wake on LAN” setting, which is generally used to allow a computer to be woken up 
remotely.
This allows you to remotely connect to a computer, without it constantly being turned on (although it has to either be 
in a 'suspend' mode, or a 'soft-off state').
"Wake on LAN" works by sending a 'magic packet' (a special network signal) to tell the device to wake up.

#### Solution
_Disclaimer:_ I was able to resolve this issue by deactivating "Wake on LAN" entirely.
Luckily for me, that's a setting I don't need for my laptop.
If you do need that functionality, keep looking for another solution elsewhere!

**Testing the solution**

Using `ethtool`, I could check my network configuration with `ip a`.
I found the ethernet interface ID, which looked like `enpxxxxxx`.
According to the Linux predictable network interface naming convention, `en` represents an ethernet connection, and `p`
indicates a physical hardware connection.

By running, `sudo ethtool enpxxxxxx` (replacing the final part with your own interface ID), you should get a response
including lines like:

```
Supports Wake-on: pumbg
Wake-on: g
```

This represents the available Wake on LAN options, as well as the currently selected one (`g`).
To disable Wake on LAN entirely, you can run: `sudo ethtool --change enpxxxxxx wol d`

Now, you should be able to successfully suspend your device!

**Full implementation of the solution**

Unfortunately, this command isn't persistent, and needs to be run every time your device is powered on...
Here's how I did that:

1. Create a new `systemd` service, by creating the file `/etc/systemd/system/wol.service`, with the 
following contents:

```
[Unit]
Description=Disable Wake On Lan

[Service]
Type=oneshot
ExecStart = /usr/sbin/ethtool --change enpxxxxxx wol d

[Install]
WantedBy=basic.target
```

2. Reload the `systemd` service to apply the new service

```
sudo systemctl daemon-reload
```

3. 'Enable' the service, which means it will be automatically started on boot:

```
sudo systemctl enable wol.service
```

4. Optionally, start the service immediately:
```
sudo systemctl start wol.service
```

_**Issues with systemd:**_
If you're using a system that relies on `/etc/network/interfaces` to configure your network (like older versions of 
Debian-based distributions), you should add the command to the `iface` configuration. 
To keep things simple, I haven't included those instructions here, so you'll have to keep looking for how to configure
that.

**Optional read: investigating the BIOS configuration**

Across the various forum posts I read, there were a lot of comments about "Wake on LAN" being a BIOS setting versus an
Operating System setting.
So, I looked into the settings at both the BIOS and Operating System levels.
My default BIOS settings included:

* Wake on LAN enabled only when plugged in
* Wake on LAN from dock was `True`

I tried various combinations of changing these settings, none of which worked, so I moved onto the Operating System 
settings.
That solution is what is described above.

#### References
Thanks to the following pages which helped me to diagnose and resolve this issue!

* https://askubuntu.com/questions/1310359/wake-on-lan-with-suspend-ubuntu-server-20-04
* https://necromuralist.github.io/posts/enabling-wake-on-lan/
* https://www.thomas-krenn.com/en/wiki/Predictable_Network_Interface_Names

<!-- + text + -->