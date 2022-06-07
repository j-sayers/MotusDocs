---
description: >-
  False detections (a.k.a. false positives) are a frequent occurrence in radio
  tracking. In fact, any tracking technology has erroneous data that must be
  handled in a unique manner.
---

# False Detections

## How do false detections occur

&#x20;In Motus, there are multiple ways in which false detections can occur. The three main methods are:

* **Environmental noise:** this can be anthropogenic or natural (from space!).
* **Bad metadata:** researchers haven't entered deployment information for their tags so our system doesn't know they are deployed. Detections of the tags are therefore interpreted as a different (false) tag.
* **Tag aliasing:** a large number of tags (10+) are all deployed at the same location and time and their signals overlap. Their close physical proximity means the signals emitted by the tags appear very similar to the receiver, making it hard to tell them apart. This can result in the mixing of multiple tag signals which may be mis-interpreted as another tag that is not actually present. [Read more here.](../../tags/tag-aliasing.md)

## How are false detections dealt with?

Public data has been processed using broad filters based on theoretical flight speeds, logical geographic/time sequences, and at least 3 consecutive tag bursts at a single station. Individual tracks have not been inspected for accuracy. We also apply manual filters for known cases of false detections.

Researchers inspect and filter their data based on [guidelines provided in the Motus R Book](https://motuswts.github.io/motus/articles/05-data-cleaning.html).&#x20;

### How public track data is calculated

Tracks are based on the shortest possible paths between detections, and thus are unlikely to represent the true path unless the estimated speed is fairly high. Distance between detections is based on the location of the receivers, which doesn't take into account the detection ranges of the antennas (as much as 20km when conditions are good). Therefore, the estimated distance between detections may be too large by as much as 40km (when two unobstructed antennas are pointed directly at each other), and thus when the receivers are less than 100km apart the estimated minimum speed may be unrealistically high. Speed estimates for receivers more than 100km apart seem to be reasonably accurate. False detections happen sometimes (especially when equipment is faulty, a receiver is near a radio source, or a tag pulse pattern is ambiguous), but rarely last even a second. Very short detections can be filtered out (or not) in the settings.
