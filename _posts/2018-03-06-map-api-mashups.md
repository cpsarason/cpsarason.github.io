---
layout: post
author: Chistian P. sarason
date: 2018-03-06
title: Mashing up Map applications, Part I
tags: living-in-the-future jupyter tech4good maps
---

## Hacking the Planet, Inc. Ship Detector

1. zoomed in on Elliot Bay w/ Planet Explorer.
2. Dragged box around Elliot Bay to get georeference.
3. Screenshot the box (yes, this is naughty, but wanted to do quick and dirty)
   converted the PNG to TIF:

```
$  convert elliot_bay_2016_07_mosaic.png elliot_bay_2016_07_mosaic.tif
```

4. Added bounding box and georeference (guessed EPSG:4326. Score!)

```
$ gdal_translate  -a_ullr -122.42674827575682 47.634048474793985 -122.33199119567873 47.57617830178651 -a_srs EPSG:4326 elliot_bay_2016_07_mosaic.tif elliot_bay_2016_07_georef.tif

Input file size is 552, 501
0...10...20...30...40...50...60...70...80...90...100 - done.
```

5. Swapped in my new "georeferenced" tif image for the one in Planet's Ship
Detector notebook

6. Changed the tolerance on area to be >10. Success!

## Proof is in the pudding

### Input

![Input Image of Elliot Bay]({{"/assets/images/elliot-bay-ship-detector-input.png" "Screenshot from Planet Explorer of Elliot Bay" |absolute_url}})

### Output (with ships masked)

![Output Image of Elliot Bay]({{"/assets/images/elliot-bay-ship-detector-mask-labeled.png" "Screenshot from Planet Explorer of Elliot Bay" |absolute_url}})

### Georeference Test

To test that I got things roughly right, threw my hacked geotiff into QGIS to check
registration. Looks pretty good. Next, I want to take the output lat/lons and
add them to a leaflet map as markers (with the satellite image overlay).

![Referencing test of Elliot Bay]({{"/assets/images/qgis-elliotbay-overlap.png" "Screenshot from Planet Explorer of Elliot Bay" |absolute_url}})

## Thought of the day
Obviously this write up is a quick and dirty process --- the amazing part of the
Planet API is they make it very easy to automate this process, allowing for
ongoing monitoring of various locations and algorithm development for different
use cases. Neat stuff!
