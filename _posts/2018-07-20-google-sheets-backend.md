---
layout: post
author: Christian P. Sarason
date: 2018-07-20
title: Using Google Sheets API as a simple observation database
tags:  tech4good timeseries mapbox OrcaMap
---
# Spreadsheets are the zero-order user interface

![A Google Sheet can be a quick and easy database for your map app]({{"/assets/images/orcamap-google-sheet-snap.png"}})

Sometimes you just need something simple. In playing around with node.js and
MapBox, so far I have just jammed everything into local geoJSON files and/or
increased them in size with javascript. This makes it fast and easy to develop,
but in some cases leads to *very bad things* (blowing up the size of the page,
for example, should you inadvertently keep appending to an array).

I was inspired by a talk that I saw at the May 2018 [CUGOS](https://www.cugos.org)
meeting, where [Sam Mathews](https://www.mapbox.com/about/team/sam-matthews/) gave
a quick talk about using the Google Sheets API to save
[geojson data to a spreadsheet.](https://github.com/cugos/gus-api). I thought
it was a cool concept and I love Sam's quote that "spreadsheets are always my
first default interface for data entry". Basically everyone knows how to use
at spreadsheet, so while things like [InfluxDB]({{"2018/05/14/influx_db_scratchnotes.html"|absolute_url}})
