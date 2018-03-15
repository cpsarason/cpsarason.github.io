---
layout: post
author: Chistian P. sarason
date: 2018-03-09
title: Tapping into a geyser of deep sea data
tags: living-in-the-future tech4good ocean visualization
---
## NEPTUNE, 20 years later

When I was graduate student at UW in the mid-90s, some blarney beer-filled
conversations about "What if we..." turned into a passion for
[John Delaney](https://www.ocean.washington.edu/home/John+Delaney),
who proceeded to suck in a bunch of other folks around the idea of creating
the equivalent of a deep-space telescope, but pointed at the small tectonic
plate just off our coast. Nearly 20 years (and a boatload of work) later,
the NSF sponsored OOI Cabled Array is operational off of the Washington and
Oregon coasts! A couple of weeks ago I spent 3 days in MSB 123,
the same room where I defended my Masters, and learned the ins/outs of how
to access the data that is streaming in from the installation at the
[Cabled Array Hack Week (CAHW)](https://github.com/oceanhackweek/CAHW2018_Materials).

## Making some interesting plots

There is a ton of different data streaming in from the cable --- with everything
from humdrum <em>C</em>onductivity, <em>T</em>emperature, <em>D</em>epth (CTD)
data to more esoteric physical and biological measurements like Nitrate, Oxygen,
and Spectral Irradiance. Also accompanying these measurements are a plethora of
acoustic sensors, both active (ADCP) and passive (hydrophones). I chose to use
the CAHW to learn how to access the data and gain access to as much data as I
could reasonably use as a basis for polishing up my dataScience techniques.

### Plotting up temperature and salinity

First, I decided to plot up a simple color-coded scatter plot of the measurements
over time. The tools have become so much easier than when I was doing a lot of
this kind of analysis at UW and 3TIER as a scientific programmer --- now dates
are automagically handled and the netCDF support in python is really good.

```python
# Now, more complete colored scatter plot, with data plotted
# on a depth vs. time axis.

fig,(ax1,ax2) = plt.subplots(nrows=2,ncols=1)
fig.set_size_inches(16,9)

# plot temp and salinity curtain plots
ax1.invert_yaxis()
ax1.grid()
ax1.set_xlim(ds_time[0],ds_time[-1])
sc1 = ax1.scatter(ds_time,pressure,c=temperature)
ax1.set_xlabel('Date')
ax1.set_ylabel('Pressure (dbar)')
ax1.set_title('Temperature (degC)')
cb = fig.colorbar(sc1,ax=ax1)

ax2.invert_yaxis()
ax2.grid()
ax2.set_xlim(ds_time[0],ds_time[-1])
ax2.set_xlabel('Date')
ax2.set_ylabel('Pressure (dbar)')
ax2.set_title('Salinity (psu))')
sc2 = ax2.scatter(ds_time,pressure,c=psu)
cb2 = fig.colorbar(sc2,ax=ax2)
plt.show()
```
