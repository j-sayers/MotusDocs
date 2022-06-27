# How Data are Processed

## Overview

There are multiple data sets available from Motus which are each processed differently based on the type of receiver they were collected from as well as the type of transmitter that is being listened for (Lotek or CTT). A diagram of how these data are processed can be seen in the [Data Processing Pipeline](how-data-are-processed.md#data-processing-pipeline).&#x20;

### Lotek tag data

Lotek tags emit a pulse position modulated signal (see [how tags work](../tags/how-tags-work.md#lotek-radio-tags)) which is recorded as a collection of time-stamped "pulses" on SensorGnome and CTT SensorStation receivers. A large list of these pulses are then processed by the [<mark style="color:green;">**tag finder**</mark>](../tags/appendix/tag-finder.md) algorithm which essentially looks at the timing between individual pulses ("pulse intervals") and matches them to a list of known Lotek tag IDs. Lotek receivers do not record individual pulses, but actually decode the Lotek Tag IDs internally and record the timing and ID of the tag detection. At this time, the Motus is able to decode tag IDs using tag finder on their servers due to an existing NDA between Birds Canada and Lotek, but otherwise this information is kept secret.&#x20;

## Tracks

### How public track data is calculated

Tracks are based on the shortest possible paths between detections, and thus are unlikely to represent the true path unless the estimated speed is fairly high. Distance between detections is based on the location of the receivers, which doesn't take into account the detection ranges of the antennas (as much as 20km when conditions are good). Therefore, the estimated distance between detections may be too large by as much as 40km (when two unobstructed antennas are pointed directly at each other), and thus when the receivers are less than 100km apart the estimated minimum speed may be unrealistically high. Speed estimates for receivers more than 100km apart seem to be reasonably accurate. False detections happen sometimes (especially when equipment is faulty, a receiver is near a radio source, or a tag pulse pattern is ambiguous), but rarely last even a second. Very short detections can be filtered out (or not) in the settings.

## Data Processing Pipeline

Data are processed differently depending on the type of receiver and tag. Data received from Lotek tags are processed on the Motus server where it matches the ID and burst intervals to known tags within the system. Similarly, CTT tag data are processed on CTT's servers where it can be validated agains its own list of tag IDs which have been manufactured. Due to these differences in data processing, data uploaded to Motus - either manual or automated - need to be routed to the correct server based on its contents.

The three diagrams below outline the data processing pipelines for [**the three types of receivers** ](../stations/station-equipment/receivers.md)used within the Motus network.

![SesnorGnome Data Processing Pipeline](<../.gitbook/assets/SensorGnome Data Processing Pipeline Diagram.png>)

![CTT SensorStation Data Processing Pipeline](<../.gitbook/assets/CTT SensorStation Data Processing Pipeline Diagram.png>)

![Lotek SRX Data Processing Pipeline](<../.gitbook/assets/Lotek SRX Data Processing Pipeline Diagram.png>)
