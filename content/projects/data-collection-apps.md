---
title: "Building Data Collection Apps"
date: 2021-12-01
featured: true
description: "I implemented a process for creating apps for geospatial data collection and surveying, integrating with the open source QGIS application."
tags: ["Geospatial", "Planning", "Research and Development", "QGIS"]
image: "/images/app_data_collection.webp"
link: "https://mrcagney.works/auditing-accessibility-on-your-phone.html"
fact: ""
weight: 500
sitemap:
  priority : 0.8
---

In my work at [MRCagney](https://www.mrcagney.com/), we would occassionally undergo spatial data collection activities. 
This wasn't part of our core work and would happen only a few times per year. We had never found the opportunity to 
invest the time to develop an app-based approach for data collection activities (and were instead still using pen and 
paper!). I used the opportunity of an upcoming project along with some free time to investigate the options for 
app-based spatial data collection. 
Although I knew ArcGIS had enterprise solutions, I was particularly interested in what we could do with QGIS, the open 
source alternative (and my preferred geospatial software).

After some research and trials, I found that I could set up a standard QGIS project with some additional configuration, 
and then easily deploy that project to one of two data collection apps: [Mergin Maps](https://app.merginmaps.com/) 
or [QField](https://qfield.org/).

This changed the way we did any projects requiring data collection and enabled us to position ourselves more strongly 
for work like this. It also encouraged us to strengthen the quality of how we presented and shared the data collection 
to our clients afterwards, by applying additional post-processing to the data. Following these upgrades to our data 
collection process, we would provide both a set of automated reports and an interactive web app with maps to our clients.

The image below shows to screenshots of a data collection project in Mergin Maps: the left side shows the map input page 
and the right shows the input form to select characteristics of data points.

![Screenshot of the map and input form in the data collection app](/images/app_data_collection.webp)