---
layout: post
author: Christian P. Sarason
date: 2018-05-14
title: Using a InfluxDB to Manage crowdsourced Whale Observations
tags:  tech4good timeseries InfluxDB
---
## On ocean data, timeseries and the wrangling of observations

```
(warning: this post is kinda wonky and probably filled with far too many generalizations. YMMV)
```

Ocean science is challenging for many different reasons. Some of these are
fundamental: the ocean is always changing and responding to different inputs
(weather, climate, river inputs, geology, plate tectonics, biology, chemistry)
and to fully understand the system you need to take a lot of different things
into account. Some things we can model very accurately (tidal heights) and
others are a bit more tricky, often pushing modeling systems to the brink.

In the end we need always ground our modeling efforts in actual *observations*, and
as a result we often rely on using time and space as the fundamental ways to
structure our observations. *Raw* observations almost always have a spatial
component (lat, lon, depth) as well as a time (UTC). *Processed* observations
are usually "binned", allowing us to look at averages (say, for over a square
kilometer patch, or by time into monthly averages). Anyone who has processed
log files for a website running in production, or who has analyzed data for a
business knows this process well --- questions like "what is Q4 revenue" or
"how many hits/day is our site receiving". Much of the work of a data analyst
or data scientist is figuring out how to process the raw information into
something more manageable to think about.

## Why use a timeseries DB?

Part


## Some raw notes from playing around with InfluxDB

```
select intensity as "verified_intensity" into limeKiln from limeKiln where listener='AutoDetect' and intensity > 100 group by *
```
