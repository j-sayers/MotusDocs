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

## Identifying False Detections

There are several methods we use to identify false positives, but for most the first indicator will be intuition. That is, the context of a detection can sometimes provide the most clues, or at least indicate that certain data should be further scrutinized. Typically, certain stations will be particularly susceptible to producing false positives which results in a cluster of detections by different animals at that location.

### Examples of false positives in data

#### Tracks Map

Tracks are most obviously false when there are long distance East-West movements, or during the non-migratory period, North-South movements. Some false detections occur at certain stations multiple times, creating a back-and-forth movement which looks false. In other instances, the animal has merely moved out of range and is likely false – that is, unless the animal was tagged as part of a vagrant study (in which case we don't expect them to be in range!).

![Example irregular track where false positives are evident by multiple East-West movements to certain sites](<../../.gitbook/assets/image (8).png>)

#### **Detection timelines**

Detection timelines are a very useful tool for determining when stations are functional as well as when they are experiencing a noise event. These show exactly when detections occur as well as the general level noise in the radio environment.&#x20;

Detection timelines can also provide an indication as to whether a false detection has occurred as a result of environmental noise or whether it was caused by tag aliasing:

* **Environmental noise** will look like a spike in tag detections, where several tags that were never detected before are all detected at the same moment and then are usually never detected again. It is common for a noise event occur when no other tags are being detected, making them stand out.
* **Tag aliasing** will only occur when _multiple other real tags_ **** are present and being detected. This is because aliasing is a result of a mis-interpreted tag signal. Aliasing usually looks like one to a few tags which are detected at the same time as other tags which are known to be present (i.e., were deployed nearby). Detections of aliased tags always occur less frequently than detections of real tags, but they can still sometimes be detected repeatedly over several days.

{% hint style="info" %}
Not sure where to find these timelines? [See our chapter on detection timelines.](../../project-management/station-management/detection-timelines.md)
{% endhint %}

## Reporting

We want to know when false detections are found in the **public dataset.** For data downloaded via the [Motus R Package](https://motuswts.github.io/motus/), we only want to know if false data is found where `motusFilter == 1`. That is, we provide all data (including false positives) in the data downloaded via the Motus R package so that researchers can scrutenize data we've flagged as "false", but that anyone using those data can still use our filters by filtering for data where `motusFilter == 1`.&#x20;

For reporting, send us an email with a table (or a list) that includes the following information about each false detection:

* Tag deployment ID
* Station deployment ID&#x20;
* Justification for removal
* Suspected cause of false detection.
* The date the false detection was found
* Observer name
* Any additional comments

