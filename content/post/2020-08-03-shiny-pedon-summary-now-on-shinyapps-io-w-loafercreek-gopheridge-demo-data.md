---
title: 'Shiny Pedon Summary: Loafercreek & Gopheridge demo'
author: Andrew G. Brown
date: '2020-08-03'
slug: shiny-pedon-summary-now-on-shinyapps-io-w-loafercreek-gopheridge-demo-data
categories:
  - R
  - shiny
  - aqp
  - flexdashboard
tags: [demonstrations]
---

This is the Shiny "flexdashboard" version of the "pedon summary report" originally developed by Dylan Beaudette. I have developed and refined this dashboard periodically over several years. I developed it initially as a very simple interface to _semi-automate_ viewing profile sketches and report generation based on mapunit, series name and taxon kind. 

https://brownag.shinyapps.io/ShinyPedonSummary/

This tool has been part of the ncss-tech `soilReports` package for a while now, but recent revisions improve efficiency and produce static output matching the original report Dylan developed. 

Unfortunately, the "Export Report" button does nothing on the web-based demo, so if you are interested in that -- you will need to set up **R** and `soilReports` to try it out ;)

![The Shiny Pedon Dashboard is centered around the "sketches" made with the plot method for SoilProfileCollection objects from aqp.](/post/2020-08-03-shiny-pedon-summary-now-on-shinyapps-io-w-loafercreek-gopheridge-demo-data_files/shinypedonsummary1.png)

The Shiny dashboard, implemented with the `flexdashboard` package, is a shiny runtime output type that allows me to easily add markup for tabbed views, the left-hand "Input" pane, etc. These features allow the user to perform arbitrary filtering of the input pedon data on a variety of common attributes (mapunit symbol by overlay with input shapefile, taxon name, local phase, taxon kind, User Pedon ID). Typically, the report is run on a machine with a local NASIS database containing (potentially many) pedon descriptions. The filtering allows smaller relevant sets of data to be grouped together. In principle any sort of geographic boundary could be used as the input shapefile, but it is often practical to use SSURGO MUSYMs as strata.

Quantitative summaries of horizon morphologic data (clay, sand, fragments etc.) are using quantiles and defined probability levels for low-RV-high. The default values are `0.05`, `0.5` (median) and `0.95` -- which conceptually excludes 5% on each "tail" of the data.

Tabs make quickly switching through attributes and graphical output easy. Regular expression-driven filtering ensures you can make many combinations and exclusions to get your data filtered the way you need.

Dylan's function prepares a variety of tabular and graphical data from an input `aqp` _SoilProfileCollection_ -- typically from NASIS pedons. The individual outputs from the summary function (elements of a list) are the "tabs" in the dashboard and the sections within the static report. In the demo hosted on shinyapps.io, I have combined two common datasets from the `soilDB` package (`loafergopher`: `loafercreek` + `gopheridge`??) to provide several series and components worth of information to "sift" through in the demo of the report.

![Extending the capabilities of the report with interactive widgets has only begun to be explored with the mapview package. Much useful information about profiles in a SoilProfileCollection can be determined by the filter-pan-click method](/post/2020-08-03-shiny-pedon-summary-now-on-shinyapps-io-w-loafercreek-gopheridge-demo-data_files/shinypedonsummary2.png)
There are a couple drop-down boxes that will allow you to change the thematic attribute and modal pedon. These add helpful visualizations and additional tabular output for comparing pedons across multiple attributes and/or selecting component pedons.

The README provides a very brief description of what the different parts of the interface are and a walk through of usage.

https://github.com/ncss-tech/soilReports/tree/master/inst/reports/region2/shiny-pedon-summary

But, if that does not answer your questions, or you have ideas/requests, check out the `soilReports` issues page on GitHub: https://github.com/ncss-tech/soilReports/issues


