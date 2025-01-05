---
title: "Multispecies Tree Carbon Dashboard for New Zealand"
date: 2024-12-18
featured: true
description: "I converted a complex forestry model built in Excel and VBA into a Python model.
This involved completely reverse-engineering the spreadsheet model and restructuring it's implementation in a Pythonic
way.
I then designed and built an interactive dashboard to create a user-friendly version of the dashboard that would be more
accessible to users with limited forestry experience.
I followed an interactive dashboard design process with my colleagues and client, to make the web app easy to use and 
with minimal 'barriers to entry'."
tags: ["Dashboard", "Data Visualisation", "Data Science", "Python"]
image: "/images/multispecies_dashboard.jpeg"
link: "https://multispecies.nz/"
fact: ""
weight: 500
sitemap:
  priority : 0.8
---

[Scion](https://www.scionresearch.com/) in New Zealand has a very complex [Multi Species Carbon Calculator](https://fgr.nz/tools/multi-species-carbon-calculator/)
spreadsheet model.
This model predicts growth metrics for forest plantations in New Zealand, considering different tree species, forest
location, and silvicuture (pruning and logging) regime.
The growth metrics that are estimated include tree height, cross-sectional area, stem volume and sequestered carbon.

In my work with [Carbon Critical](https://www.carboncritical.org/), I was tasked with converting the spreadsheet model
to Python and building a dashboard out of it.
The purpose of this was not to replace the spreadsheet model, but to supplement it with a less technical, more 
user-friendly iterface.
There were two key phases of work in this project:
* Reverse-engineering and reimplementing the carbon calculator in Python
* Designing and building a Dashboard as a web-app for public consumption

This was a complex project that required me to reverse-engineer the spreadsheet model, which consists of several VBA
modules that apply forestry growth models.
As both the spreadsheet and Python models would continue to be maintained after this initial project, I had to determine 
which parts of the code were necessary for the output metrics we required and which parts could be excluded from the 
Python model.
The spreadsheet model was well constructed, but relied on features of VBA that are not available or not suited to a 
Python model.
Those features included the reading and writing of interim results in spreadsheet tables, and the use of global 
variables across modules.
This meant that building a Python version of the model required me to fully understand the VBA model to then be able to
implement it in a Pythonic way.

The second part of the project was to design and build a dashboard web-app to be made available to the public.
I followed an iterative design process with both the team at Carbon Critical and our clients at Scion.
Through these iterations, we landed on a design that achieved a good balance of simplicity for users who aren't skilled
in data, programming and/or forestry, with meaningful inputs and outputs for the growth model.
Some of the key design features of the dashboard are:
* A clear grid-based layout that dynamically adjusts for different screen sizes
* Ability to add and remove forestry scenarios at will, with helpful error or warning messages for incomplete scenario
definitions
* Default parameters for planting density and silviculture regime based on selected tree species
* Interactive plot with hover info and ability to show/hide scenarios and error margins
* Export functionality for downloading the scenario inputs and outputs, so they can also be copied across and run in the 
full spreadsheet model

I built the initial version of this dashboard web-app, however, it has since been updated further by others at Carbon 
Critical.

![Screenshot of the multispecies carbon dashboard](/images/multispecies_dashboard.jpeg)