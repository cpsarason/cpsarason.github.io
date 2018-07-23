---
layout: post
author: Christian P. Sarason
date: 2018-07-20
title: Using Google Sheets API as a simple observation database
tags:  tech4good timeseries mapbox OrcaMap
---
# Spreadsheets are the zero-order user interface

![A Google Sheet can be a quick and easy database for your map app]({{"/assets/images/orcamap-google-sheet-snap.png"}})

Sometimes you just need something simple. In playing around with Node.js and
MapBox, so far I have just jammed everything into local geoJSON files and/or
increased them in size with javascript. This makes it fast and easy to develop,
but in some cases leads to *very bad things* (blowing up the size of the page,
for example, should you inadvertently keep appending to an array).

I was inspired by a talk that I saw at the May 2018 [CUGOS](https://www.cugos.org)
meeting, where [Sam Matthews](https://www.mapbox.com/about/team/sam-matthews/) gave
a quick talk about using the Google Sheets API to save
[geojson data to a spreadsheet.](https://github.com/cugos/gus-api) I thought
it was a cool concept and I love Sam's admonition to practicality, "spreadsheets are always my
default interface for data entry". Basically, everyone knows how to use
at spreadsheet, so while things like [InfluxDB]({{"2018/05/14/influx_db_scratchnotes.html"|absolute_url}}) are super
powerful and fun to play with, when developing a prototype to share out in the
world, all of a sudden you need to manage user accounts, security, blah, blah,
blah. I can do all that, but really just want a place where multiple users can
share some prototype data and collaborate while we focus on the UX of the page
instead of the IT nitty gritty.

Enter the Google Sheet API! It is pretty easy to get started, and has the benefit
that you can have stuff password protected, with user management controlled by
sharing the sheet with your colleagues. This was a perfect fit for the OrcaMap
prototype I have been working on for the good folks at [OrcaSound](https://www.orcasound.net).

![OrcaMap observation prototype]({{"/assets/images/orca-map-prototype.png"}})

This prototype was designed to be a quick and easy way to log orca locations.
(the locations are all bogus --- there are *not* orca swimming around Harbor
Island's shipping terminal!). The data is somewhat sensitive, so we want to
limit access as well as provide for a verification step (to keep bad data
from entering the map). The best part? Google kindly provides a very
straightforward [Sheets API Quick Start](https://developers.google.com/sheets/api/quickstart/js)
guide, and it is very close to plug/chug.

Changes in the sheet (like notes and/or verification status) are immediately
incorporated into the map interface, since the javascript is building the geoJSON
for MapBox on the fly. I'm sure there is a more straightforward way to do this
using MapBox and/or other tools, but this implementation was dead easy and
pretty performant (and lets me manage user access using Google's UI, instead of
having to re-invent it.) Cool stuff!
