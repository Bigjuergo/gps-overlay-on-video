[![Build Status](https://travis-ci.org/peregin/gps-overlay-on-video.svg?branch=master)](https://travis-ci.org/peregin/gps-overlay-on-video)
[![Codacy Badge](https://api.codacy.com/project/badge/grade/8951fae912144fc587db33b27e8fb1d7)](https://www.codacy.com/app/peregin/gps-overlay-on-video)
[![codecov.io](https://codecov.io/github/peregin/gps-overlay-on-video/coverage.svg?branch=master)](https://codecov.io/github/peregin/gps-overlay-on-video?branch=master)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

GPS data overlay on videos
==========================
_The Ultimate Cycling Software_

The idea came after I bought a [GoPro](http://gopro.com/cameras/hd-hero3-silver-edition) camera and started to record
some of my rides with the bicycle which were also tracked with a GPS device.
For tracking the rides I was using the [Strava](http://www.strava.com) application on my phone
or a [Garmin Edge 510](http://www.dcrainmaker.com/2013/01/garmin-edge-510-in-depth-review.html).
After watching the videos I was asked why I'm not showing the speed and altitude information overlaid onto video?
Cool, great idea, I wanted to add all kind of telemetry data acquired via the GPS onto the video, but couldn't find a
software for it, running on my Mac. So I decided the write one :)
The generated video is able to show the current speed or the actual elevation information, eventually the grade of the slope when climbing 
a steeper section or the current heart rate zone. 
The main focus is on cycling videos, but with small effort, different gauge templates it is easy to create dashboard for different type of 
activities.

Example of videos generated with the tool, links to youtube:

[![Gurten Classic 2015](http://img.youtube.com/vi/tVCgP3Xh250/1.jpg)](https://www.youtube.com/watch?v=tVCgP3Xh250)
&nbsp;[![Zugerberg Classic 2014](http://img.youtube.com/vi/N74yLpdebJ8/1.jpg)](http://www.youtube.com/watch?v=N74yLpdebJ8)
&nbsp;[![Uetliberg Loop 2014](http://img.youtube.com/vi/0giJlMyX59I/1.jpg)](http://www.youtube.com/watch?v=0giJlMyX59I)

Screenshot of the tool:

![latest screenshot](https://raw.github.com/peregin/gps-overlay-on-video/master/doc/evolution/latest.jpg "latest screenshot")

## Basic requirements
Small list of wishes to achieve:
* show the video file and the track on the map to help synchronizing (shifting) the gps data to the beginning of the video
* add various gauges (drag'n drop into the video panel) like: speed, cadence, heart rate, altitude, acceleration, temperature, etc.
* once the gauges were added and adjusted (the size and position) allow to save the configuration as a template, so next time
it is easier to just load the template and create the new video
* and the final bit, export (or generate) to newly created video with the desired gauges. 

All the information is extracted from the gps data, since mainly the coordinates and timestamps are known, it is easy to calculate
* distance
* speed
* acceleration
* direction (compass)
* provide charts about the elevation
* etc.

Telemetry data sample collected with a Garmin device (Edge 820):
```xml
<trkpt lat="47.1512900" lon="8.7887940">
  <ele>902.4</ele>
  <time>2017-09-24T06:10:53Z</time>
  <extensions>
    <power>205</power>
    <gpxtpx:TrackPointExtension>
      <gpxtpx:atemp>8</gpxtpx:atemp>
      <gpxtpx:hr>160</gpxtpx:hr>
      <gpxtpx:cad>90</gpxtpx:cad>
    </gpxtpx:TrackPointExtension>
  </extensions>
</trkpt>
```

## Credits
The application is using libraries and images created by other people or organizations:
* [JXMapViewer](http://wiki.openstreetmap.org/wiki/JXMapViewer) to show the map and the track
* [xuggle library](http://www.xuggle.com/) to decode, encode and manipulate video files
* [iconeden](http://www.iconeden.com/icon/category/free) for the beautiful icon packs they offer
* [digital true type fonts](http://www.styleseven.com/) for the gauges with seven segment display

## Resources
Useful links and information
* [Geographical distance](http://en.wikipedia.org/wiki/Geographical_distance)
* [Haversine formula](http://en.wikipedia.org/wiki/Haversine_formula) and [Versine function](http://en.wikipedia.org/wiki/Versine)
* [Slope percentage](http://geology.isu.edu/geostac/Field_Exercise/topomaps/slope_calc.htm)
* [Fonts and graphics](http://www3.ntu.edu.sg/home/ehchua/programming/java/J4b_CustomGraphics.html)

## Generating new video with gps overlay

After synchronizing the video stream with the gps track (through the shift parameter) everything is prepared to generate a new video:

![converter](https://raw.github.com/peregin/gps-overlay-on-video/master/doc/evolution/converter.png "converter dialog")

And here it is :) the first video generated with the software (Zugerberg Classic):

[![Zugerberg Classic 2014](https://raw.github.com/peregin/gps-overlay-on-video/master/doc/evolution/youtube.png)](http://www.youtube.com/watch?v=N74yLpdebJ8)

## Gauge ideas
Besides the basic gauge types (speed, cadence, etc.) showing the current value so called _chart types_ are introduced as well.
The charts are showing all the data (for example an elevation chart) and the current value.

The very early drafts on the paper, how it started:

![gauge ideas](https://raw.github.com/peregin/gps-overlay-on-video/master/doc/gauge-ideas.jpg "gauge ideas")
