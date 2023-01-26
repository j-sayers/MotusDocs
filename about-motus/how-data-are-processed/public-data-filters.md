# Public Data Filters

## Overview

Some filters are applied to Motus data that can be accessed by the public in order to limit the number of false detections that are presented. These filters are also available to collaborators who download their data from the [**Motus R Package**](https://motuswts.github.io/motus/). This chapter goes over each of these filters and how they are applied.

## **Motus filter**

This filter was the first one to be applied to the public dataset and is the most generalised of the filters. It uses cutoffs for a set of parameters based on an empirical examination of the data. These include:

* For 'noisy' sites, minimum of 5 consecutive detections
* For 'quiet' sites, minimum of 4 consecutive detections

{% hint style="info" %}
Noisy sites are categorized as stations with many runs (>= 100 in an `hourBin`) and a high ratio of runs with lengths of 2 at a given time (>= 85% per `hourBin`).
{% endhint %}

## Manual filters

There are several edge-cases where the above Motus filter above does not remove false detections which can be problematic to present to the public. Manual filters use tag deployment ID and station ID pairs to remove these bad detections. That is, for every entry in the filter it will remove all detections of the tag deployment from that station.

## Station Filters

Certain stations are especially problematic, usually because there are large numbers of tags deployed nearby the station which are all present at once (see [**Tag Aliasing**](../../tags/tag-aliasing.md)), but it can also be due to excessively noisy sites producing false detections (see [**Noisy Stations**](../../stations/station-inspection/noisy-stations.md)). They produce false detections regularly enough that we can't keep up with the manual filters.To remedy this, certain stations are flagged as 'problematic' and all detections of non-local tags are removed from public view _on the Motus Dashboard only_. Non-local tags are considered to be any tag that was deployed further than 10 km from the station.
