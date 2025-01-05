---
title: "Project Management Dashboard"
date: 2020-10-01
featured: true
description: "I co-developed a Python dashboard to support timesheet reporting and project management activities at MRCagney."
tags: ["Python", "Dashboard", "Data Visualisation"]
image: "/images/mrcagney_reports.webp"
link: "https://mrcagney.works/mrcagney-reports.html"
fact: ""
weight: 500
sitemap:
  priority : 0.8
---

MRCagney Reports, an internal project management web app, began as a personal project of mine while at [MRCagney](https://www.mrcagney.com/) 
to improve on other project management platforms I had seen and/or trialled. After struggling to review timesheets and 
budgets while managing projects, and constantly applying manual techniques for each project I managed, I decided to try 
something new. 
I created an interactive dashboard to summarise timesheets and budgets for all projects in one place.

After developing an initial prototype, I shared my concept with my colleagues and management at MRCagney and got 
approval to develop it further. There were many further developments to make, but between a colleague and myself, we developed a 
well-rounded web-app that became a very successful project management tool across the company. Some of the key features 
of our app included:

* Secure authentication using the API provided by [Xero](https://www.xero.com) (our financial and timesheeting software)
* Scheduled daily syncing with Xero, our timesheeting system, so project managers could be confident that all reports are recent
and include all timesheet entries to the same point in time
* Filters to slice timesheets by date, task, employee, and more
* Options to view the timesheets by task or employee, and in hours or dollars
* Interactive charts to further drill into the data

This project was a big learning experience for me and allowed me to implement many key software development principles, including:
storyboarding an initial design and iterating the mock designs with the leadership team before implementing; working
with third party APIs; deploying the web app to a live website; and applying good principles for programming in a team.

The following screenshot shows an example of one of the many charts that a project manager could view and use in 
MRCagney Reports.

![Example chart from MRCagney Reports](/images/mrcagney_reports.webp)