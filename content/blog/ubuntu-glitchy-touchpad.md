---
title: "Resolving Glitchy Touchpad on ThinkPad with Ubuntu"
date: 2024-12-12
featured: true
description: "My ThinkPad laptop had a glitchy touchpad with a few glitches.
When I moved the pointer across the screen in a clean movement, it would sometimes randomly apply a 'click' action partway
through the scroll.
It would also sometimes lag a lot at the start, or in the middle, of a pointer movement.
In the end, the solution was a simple driver installation"
tags: ["Ubuntu"]
image: ""
fact: ""
weight: 500
sitemap:
  priority : 0.8
---

Although a glitchy touchpad doesn't sound like the worst issue, when you don't have a mouse and you keep inadvertently
'drag and drop' files to random locations, it becomes pretty important!
That is what I was experiencing (along with the frustration of a lagging response), which led to me to seek a solution.

#### Symptom 
When using the touchpad, the pointer movements lag and sometimes receive random 'click' events partway through the 
movement.
I experienced this issue with Ubuntu 24.04.

#### Problem
Although the touchpad largely worked initially, it seems as though a driver may be required for performance.

#### Solution
Install the following driver:

`sudo apt install xserver-xorg-input-synaptics`


