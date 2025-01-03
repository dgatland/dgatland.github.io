---
title: "Connecting to Deutsche Bahn Wi-Fi, Bypassing Docker on Linux Conflicts"
date: 2025-01-02
featured: true
description: "Docker's default configuration on Linux has an IP address conflict with Deutsche Bahn's WIFIonICE. 
The conflict meant that I couldn't connect to the WIFIonICE.
This blog post describes how I was able to resolve the issue."
tags: ["Ubuntu"]
image: ""
fact: ""
weight: 500
sitemap:
  priority : 0.8
---

One cold winter's day, I boarded a long-distance train towards Berlin and pulled out my laptop to start work for the day.
Only to be surprised that the Wi-Fi was broken!
After testing the connection from my phone, I discovered that this must be due to some Ubuntu configuration issue.
So, into the rabbit hole of Stack Overflow posts I dived, to see if this was fixable.
And it was!
This blog posts outlines what causes the issue, and how I was able to resolve it.

### Symptom
When you attempt to connect to “WIFIonICE”, the sign up page doesn’t load; and when you manually go to the sign up page 
(https://login.wifionice.de), the page won’t load. 

I experienced this issue with Ubuntu 24.04 and Docker version 27.4.1 (_spoiler alert, Docker was the cause!_).

### Problem
Docker's default configuration on Linux uses the IP range `172.17.0.0/24` to create local network bridges between 
containers. 
This means containers can communicate over that network, and any network requests in that range will be redirected to 
Docker and won't leave the device.
This can create conflicts with other network services that use that IP range, such as Deutsche Bahn's WIFIonICE which 
uses the range `172.18.0.0/16`.
This conflict prevents the Wi-Fi's login page from loading properly, and therefore prevents the device from accessing 
the Wi-Fi.

### Solution
The solution is to stop Docker, prune the (custom) network bridges, and clear the overlapping IP address. 
If you need to use Docker on the train, you can also define a custom Docker configuration so that it uses a different IP
range.

##### View your current network configuration
Run `ip a` (or `ifconfig`) to view the current network interface configuration.

As well as `docker0` you will see one or more interfaces like `br-xxxxxxxx` which are the network bridges from 
Docker. 
One of these interfaces might be using the `172.18.0.1` address, causing the conflict.

##### Stop the Docker network connections
Stop these docker networks with `sudo ifconfig docker0 down` (and equivalent for the other network bridges).

Then run `docker network prune` to clear those interfaces from the system entirely. 

Note that any network bridges that are removed may create errors when trying to run some docker containers in the 
future, because they will try to connect to a missing container.
If that happens, you can rebuild the networks with `docker compose up <container_name> --force-recreate`.

##### Optional: to use Docker while connected to WIFIonICE
To avoid the issue in the future, or to use Docker while connected to WIFIonICE, you can redefine the default IP address
for Docker.
To do this, edit or create the Docker daemon config file, at `/etc/docker/daemon.json`, to include configuration like
the following (you can choose any suitable IP range):

```
{
  "default-address-pools":
  [
    {"base":"192.168.0.0/16","size":24}
  ]
}
```

Note that the 192.168.x.x range is widely used in home and small office networks for private IP addressing. 
Routers and other devices typically assign addresses from this range to devices on their local networks 
(such as computers or printers).

##### Restart Docker
First, make sure that all containers are definitely stopped, e.g. with `docker compose down`. 
You can also confirm this with `docker ps -a` and check that no containers are running.

Then, make sure your new daemon configuration is loaded, by running `sudo systemctl daemon-reload` 
(I'm not sure if this strictly necessary, but it doesn't hurt!).

Finally, restart Docker with `sudo systemctl restart docker`.
When Docker restarts, it should be using the network range you defined in your custom configuration file.


### References
Thanks to the following blog and support pages for helping me resolve this issue!

* https://dev.to/ingosteinke/comment/21075
* https://forum.ubuntuusers.de/topic/probleme-mit-dem-wifionice/
* https://serverfault.com/questions/916941/configuring-docker-to-not-use-the-172-17-0-0-range