---
title: "Land Use & Public Transport Accessibility Index (LUPTAI) Tool "
date: 2025-06-26
featured: true
description: "A brief introduction to the LUPTAI tool"
tags: ["Transport", "Planning"]
image: ""
fact: ""
weight: 500
sitemap:
  priority : 1.0
---

A few years ago, I came across the Land  Use & Public Transport Accessibility Index (LUPTAI) Tool. 
Having spent a lot of my time working at [MRCagney](www.mrcagney.com) thinking about analysing and visualising public 
transport accessibility, I was naturally very interested in this.
Every now and then, when talking about public transport accessibility, this methodology comes to mind, so I've compiled
some basic information about it into this blog post, as a quick reference point.

### Background

LUPTAI was originally developed to assess people's ability to access key destinations by public transport (and walking) 
journeys.
It therefore had an important dual focus on public transport, and on actual destinations that people want to go to.
The methodology was later extended to include cycling and car access too.
There are a wide range of accessibility models that have been proposed over time, and Bertolaccini et al. (2017)
include a literature review of several of these models from Australasia and globally.

### Methodology

The methodology of LUPTAI is based on a running a Monte Carlo simulation, to simulate possible destination choices and 
travel times for certain scenarios (e.g. activity type or time of the day), and then aggregating these results.
The final values that are produced by the methodology represent the average estimated travel time _to_ an activity 
_from_ an origin.
A rough overview of the methodology is as follows.

##### Data Preparation

1. Collect network data for given mode of transport (e.g. street network and/or GTFS feeds)
2. Collect destination dataset with all the locations of the destinations of interest
3. Determine _Exclusion Probabilities_ for each destination type. 
   The exclusion probability represents the likelihood that a specific destination will be _unsuitable_ for an 
   individual (in any single simulation run). 
   For example, an exclusion probability of 0.4 for hospitals means that when a person considers each individual 
   hospital, there is a 40% chance that the hospital does _not_ meet the person's needs. 
   In other words, only 60% of hospitals in the region _do_ meet the person's needs.  
     
   Bertolaccini et al. (2017) chose the following exclusion probabilities in their implementation:

    | Activity           | Exclusion Probability |
    | --------           | --------------------- |
    | Hospital           | 0.4                   |
    | Library            | 0.0                   |
    | Major shops        | 0.1                   |
    | Misc shops         | 0.2                   |
    | Primary School     | 0.2                   |
    | Secondary School   | 0.3                   |
    | Supermarket        | 0.1                   |
    | Tertiary Education | 0.5                   |
    | Welfare            | 0.0                   |
    | Employment         | 0.999                 |  
  
4. If you want to create an aggregated accessibility score across _all_ destination types, you can also assign a 
   weighting to each destination type, based on the relative importance of each activity. 

##### Monte Carlo Simulation

Once the data has been prepared, the Monte Carlo simulation can begin. 
A Monte Carlo simulation simply means to run an analysis (that has some randomness) many times, and then to collect the 
range of expected outcomes.
This typically produces some kind of distribution, which can then be used to inform subsequent models or decisions.
The following steps describe each individual simulation run, and would be run many times (e.g. 50-100). 

1. Choose the origin point, which could be the same for all runs, or could be randomised within a region of interest
2. _If analysing public transport access,_ choose a departure time from the time window of interest
3. Choose the destination type and reduce the destination points to just the _suitable_ locations by applying the 
   exclusion probability to each possible location
4. Compute the shortest path from the origin to the nearest suitable destination to estimate the travel time for this 
   run

After running the simulation the desired number of times, compare the travel time for each run to produce some 
statistics and/or a distribution of the expected travel time to the destination of interest.

### Summary

The LUPTAI methodology produces an average estimated travel time to an activity from an origin, by running many 
simulations of access to the _nearest suitable destination_, where the nearest suitable destination (and possibly other
parameters) change in every run.
The LUPTAI model has been implemented in open source models for both QGIS and Python (although I have not tried either 
of these) - see the [documentation here](https://tau-docs.tmr.qld.gov.au/luptai/) for more information.

### References

* [Evaluating the LUPTAI Accessibility Model: A Case Study of a Proposed Green Bridge in Brisbane](https://australasiantransportresearchforum.org.au/wp-content/uploads/2022/03/ATRF2017_096.pdf)  
  Bertolaccini, K., Pyrohava, S., English, P., Hickman, M., & Sipe, N. (2017)  
  Australasian Transport Research Forum 2017 Proceedings, 27 – 29 November 2017, Auckland, New Zealand
* [Land Use & Public Transport Accessibility Index (LUPTAI) Tool - The development and pilot application of LUPTAI for the Gold Coast](https://australasiantransportresearchforum.org.au/wp-content/uploads/2022/03/2006_Pitot_Yigitcanlar_Sipe_Evans.pdf)  
  Pitot, M., Yigitcanlar, T., Sipe, N., & Evans, R. (2006)     
  Australasian Transport Research Forum (ATRF), 27-29 September 2006, Surfers Paradise, Gold Coast
