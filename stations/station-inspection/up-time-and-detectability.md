---
description: >-
  This section describes how to identify when your station was powered on and
  able to detect tags.
---

# Up time and detectability

## Introduction

There is currently no single way to determine when a station was operational. This is because if there are no tags present, there will be no clear way to say tags _could have been detected._ However, it's possible to come up with a proxy for when a station could have detected tags based on when environmental noise was recorded or when other scheduled operations on the receiver were logged.

### Reboot Odometer

SensorGnomes and SensorStations will record each time the device has booted up. While this doesn't tell you when the station was last powered down, that can be inferred based on when data was last collected. It is also important to understand that even when the station is powered on, it may not be able to collect data, therefore it's helpful to check if GPS hits or antenna pulses exist.

This metric is not available for download at this time, but can be found on the top of the [deployment timeline](../../explore/detection-timelines.md#deployment-timeline) and can be helpful in diagnosing power issues stations.

### GPS Hits

Motus receivers are programmed to log a GPS hit every 5 minutes by default (should be more frequent for mobile receivers), but sometimes the GPS can miss a hit or two if few satellites are visible overhead. In addition, early GPS units (USB GPS) had a bug which caused the GPS to malfunction and stop collecting data, resulting in missing GPS hits for extended periods of time. Therefore, these data should be used in combination with other logs to determine when the station was operational rather than on its own, unless you know the GPS was not of the USB type.&#x20;

GPS hits appear as the second line on [deployment timelines](../../explore/detection-timelines.md#deployment-timeline), on [receiver timelines](../../explore/detection-timelines.md#receiver-timeline), and on[ the data dashboard](../../explore/detection-timelines.md#station-timeline). It can also be downloaded from [the 'GPS' table from the Motus database downloaded through the Motus R Package](https://motuswts.github.io/motus/articles/03-accessing-data.html).

### Antenna Pulses

Antenna pulses are a reflection of environmental noise and consist of radio pulses at the nominal listening frequency (e.g.; 166.38 MHz) which did not correspond to a known tag signature. Environmental noise is common and in some instances can be problematic, resulting in large numbers of false detections and/or expensive cellular data bills. In addition, large volumes of noise can make it less likely for real tags to be detected. You can read more about [antenna noise here.](noisy-stations.md)

The amount of noise received by any given antenna depends on a number of factors and varies widely by climate, location, time of day, and day of year. Some environments can have very low noise levels, while others are extremely high. In some cases, damaged or defective equipment can also result in low or high noise levels making it difficult to assess an individual antenna is functioning correctly based on this metric alone. [Information on assessing antenna equipment can be found here. ](antenna-inspection.md)

Antenna pulses appear after the GPS hits on [deployment timelines](../../explore/detection-timelines.md#deployment-timeline), on [receiver timelines](../../explore/detection-timelines.md#receiver-timeline), and on[ the data dashboard](../../explore/detection-timelines.md#station-timeline). It can also be downloaded from [the 'pulseCounts' table from the Motus database downloaded through the Motus R Package.](https://motuswts.github.io/motus/articles/03-accessing-data.html)

## Combining data to assess station operation

Based on the information above, GPS hits and antenna pulses can be used together to make a general assessment on when stations were operational. Hourly summaries of GPS hits and antenna pulses can be combined to determine if a station collected any data during each hour.&#x20;
