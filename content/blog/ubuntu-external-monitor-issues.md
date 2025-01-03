---
title: "Resolving Ubuntu Issues with Second Monitor (Through Docking Station)"
date: 2024-11-25
featured: true
description: "I use my Ubuntu laptop with a Dell docking station, which is connected to an external monitor. 
I was getting an intermittent error where the laptop would recognise the external monitor and act as if it was 
connected, but the monitor would not be receiving any signal. 
This (short) blog post outlines the driver updates required to resolve this."
tags: ["Ubuntu"]
image: ""
fact: ""
weight: 500
sitemap:
  priority : 0.8
---

#### Symptom 
I use my Ubuntu laptop with a Dell docking station, which is connected to an external monitor. 
I was getting an intermittent error where the laptop would recognise the external monitor and act as if it was 
connected, but the monitor itself would not be receiving any signal. 
I experienced this issue with Ubuntu 24.04, and have also previously experienced it with Ubuntu 20.04.

#### Problem
Although the Dell docking stations seem to mostly work 'out of the box', they actually require a DisplayLink driver for
full functionality.

#### Solution
Install the Display Link driver, following the [official instructions](https://www.synaptics.com/products/displaylink-graphics/downloads/ubuntu),
copied here for completeness:

1. Download the [Synaptics APT Repository from here](https://www.synaptics.com/products/displaylink-graphics/downloads/ubuntu)
2. `sudo apt install ./Downloads/synaptics-repository-keyring.deb`
3. `sudo apt update`
4. `sudo apt install displaylink-driver`
