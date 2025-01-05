---
title: "3D Modelling Forests to Create Synthetic Training Data for Machine Learning"
date: 2023-12-14
featured: true
description: "I built a 3D model for simulating pine plantations in Blender, utilising its Python integrations to enable 
the rapid generation of large datasets, varying by age, planting density and background weather conditions. These 
datasets can then be used for the research and development of vision-based machine learning algorithms."
tags: ["3D Modelling", "Research and Development", "Machine Learning", "Blender", "Python"]
image: "/images/forest_model.webp"
link: "https://www.carboncritical.org/post/3d-forest-modelling"
fact: ""
weight: 500
sitemap:
  priority : 0.8
---

As part of a research and development project at [Carbon Critical](https://www.carboncritical.org/), I built a 3D 
modelled landscape in Blender for creating simulated renders of pine plantations. 
Initially, I simulated a single pine plantation from which we could render images from different positions and angles. 
I then extended this model using Blender's Python integration to be able to simulate variations to:

* The age of the pine plantation, including both the size of trees and "tree thinning" over time.
* The planting density of trees, representing the spacing and variability of spacing between trees.
* Lighting and cloud coverage of the sky in the background.

I used these Python integrations to automatically produce a large dataset of images of pine plantations, which could
then be used for training potential machine learning models.

Visit the project link below to read a full blog post detailing this project and application.

![Screenshot of a modelled forest render](/images/forest_model.webp)