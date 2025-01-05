---
title: "Whangārei Housing Capacity and Feasibility Model"
date: 2021-05-03
featured: true
description: "I provided complex and detailed geospatial processing techniques to inform a computational model for 
estimating the capacity for supply of new housing in Whangārei. I also project managed and provided advice for the
development of that computational model."
tags: ["Geospatial", "Data Science", "Python"]
image: "/images/whangarei_housing_thumbnail.webp"
link: "https://mrcagney.works/whangarei-housing-assessment.html"
fact: ""
weight: 500
sitemap:
  priority : 0.8
---

I led the development of an online housing capacity model for Whangārei while working for [MRCagney](https://www.mrcagney.com/). 
The model computes the plan-enabled and commercially feasible housing capacity of the urban environment of Whangārei. 
It was developed to help the Council meet the statutory requirements of the National Policy Statement on Urban 
Development (2020). I was the project manager for this project and also led the data science for the data pre-processing 
elements of the project.

I developed and implemented a complex and detailed geospatial processing pipeline as 
pre-processing for our computational Housing Capacity and Feasibility Model for Whangārei District Council. The model 
takes key inputs such as the District Plan regulations and zones, current land development patterns, and financial 
housing market assumptions to estimate the potential supply for future housing across the district. The outputs include 
whether housing on a given parcel of land is enabled within the District Plan zones and specific rules, and whether it 
is likely to be commercially profitable.

The geospatial pre-processing that I implemented for this project included creating a repeatible and reproducible 
process to:

* Combine spatial and non-spatial datasets from a range of sources, such as Council's ratings database and hazard 
mapping, with the national land parcel database
* Identify and extract sub-parcels of land that are vacant and developable, with no existing buildings, hazards or 
designations overlaying them
* Compute a 'shape' metric to determine whether the parcel is of a suitable shape for development; a measure based on
the area of the largest circle that can fit entirely within the land parcel

The complex nature of some of these processes and the large datasets meant I had to rely on several advanced
processing techniques, such as parallel computing. 

The screenshot below is from the final Housing Capacity and Feasibility Model that we hosted online for Whangārei 
District Council. You can read more about the model and try a demo version of it from the project link at the bottom
of this page.

![Screenshot of housing capacity and feasibility model](/images/whangarei_housing_thumbnail.webp)