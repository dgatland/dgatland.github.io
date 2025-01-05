---
title: "Mapping Realistic Travel Time Catchments for Public Transport"
date: 2022-01-15
featured: true
description: "I developed a process for mapping realistic travel time catchments for public transport and developed 
tools in ArcGIS to automate the process of building these."
tags: ["Geospatial", "Data Science", "Data Visualisation", "Research and Development", "Planning", "ArcGIS"]
image: "/images/gradient_isochrones_hawkes_bay.webp"
link: "https://mrcagney.works/gradient-isochrones.html"
fact: ""
weight: 500
sitemap:
  priority : 0.8
---

In my public tranport planning work at [MRCagney](https://www.mrcagney.com/), I was often asked how we could better 
communicate the impacts of frequency and time of day on travel time catchments. A travel time catchment (an "isochrone") 
is a map where an area is coloured to show what places are accessible within a travel time limit from a given origin.

Traditionally, a single isochrone map would be produced for a given journey start time, e.g. 8am. It would be created for 
either a single travel time limit (e.g. 30 minutes), or sometimes for multiple travel time limits (e.g. 15, 30 and 45
minutes) that are each coloured differently to show how much further you can get with some additional time.

The selection of the journey start time in the traditional approach is crucial and can significantly impact the 
resulting isochrones. For example, if the selected start time aligns with an infrequent service, the area served by that
service would be included in the isochrone with no initial waiting time, even if it only goes once or twice a day. On 
the other hand, if the start time happens to be just after a service that goes every 15 minutes, the start of the 
journey will be penalised with a 14 minute wait (which is much longer than the average wait). In most cases,
these would happen as an accidental outcome of a chosen journey start time. However, it would also be possibly for 
someone to intentionally select a start time that encourages an outcome they have particular a interest in.

At MRCagney, we came up with several methods for addressing this, each with different advantages and disadvantages. The
method that I developed was focused on the human element of visualising, interpreting, and understanding what areas can 
be accessed within a travel time limit, with a 'turn up and go' level of service (so passengers don't need to know the 
timetable and make sure they start their journey at a specific time). Other methods we developed were more quantitative
and provided numerical benchmarks for comparison and could be analysed and aggregated in various ways.

The method I developed was called a **Gradient Isochrone**; named because the output is a map that has a gradient of 
shading based on how consistently different areas can be accessed within the travel time limit (e.g. 45 minutes), within
the travel time window (e.g. 7-8am), without planning the journey start time around the public transport schedules. 
Areas of the map that are shaded with a more solid colour can be accessed within the travel time limit for any start 
time (without planning your journey to coincide with schedules). Areas of the map that are more transparent can also be 
accessed within the travel time limit, ***but*** they do require more journey planning around the schedules to minimise wait
time. 

The image below shows an example of these isochrones for a Hawkes Bay project we did at MRCagney.

![Example image showing gradient isochrones](/images/gradient_isochrones_hawkes_bay.webp)