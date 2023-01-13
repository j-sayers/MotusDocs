# Station Status

The status of a Motus station refers to various parameters which help us diagnose its ability to detect Motus tags. There are many reasons you may want to check on the status of a Motus station. For one, it's an important part of regular station maintenance for collaborators who manage part of the Motus network. It can also be a key tool for identifying the source of data gaps.

This chapter outlines ways you can use the data dashboard to explore the status of a Motus station.



### **Station timeline**

An interactive plot of daily GPS hits, antenna pulses, and filtered tag detections at a given station. Time is plotted on the X axis and each tag or device (gps/antenna) are plotted as a categorical variable on the Y axis. Data are represented as coloured bars with the intensity increasing with the count of detections for that given variable. An additional row on the top of the plot displays the deployment periods as coloured boxes (colour of box changes with each deployment).

#### Uses

* Checking when a station was functional and able to detect tags
* Identifying noisy antennas/sites
* Looking for noise events which may have resulted in false positives

**Location**

This plot is available in the public data under explore data after any station has been selected. On a station summary page, click on the 'Status' tab next to the 'map' tab.

![](<../.gitbook/assets/image (3).png>)

#### Navigating&#x20;

* There are two parts: the main plot on top and the smaller 'brush' plot on the bottom for navigation.&#x20;
* On the main plot you can zoom in and out (scroll the mouse wheel) and click and drag your mouse to move it horizontally.&#x20;
* Hovering your mouse over the main plot gives you specific numbers for each variable on the day your hovered over.&#x20;
* The 'brush' plot is used to more quickly zoom into specific areas of the plot. This can be done by clicking and dragging on the plot to draw a box around the data you wish to zoom into.&#x20;
  * Once the plot is zoomed in, you can click and drag this box to move it around.

#### Interpretation

* GPS hits are not collected by all receivers equally; some stations may present frequent gaps in these data. SensorGnomes frequently have malfunctioning GPS units which make them unreliable. Lotek receivers do not always collect GPS hits.
* Antenna activity is a reflection of environmental noise and amount detected depends largely on the frequency. Activity on 434 MHz antennas (with the 'L' prefix) or on Lotek receivers are actually showing instances where false detections have occurred. On the other hand, activity on all other antenna frequencies are showing raw pulses on that frequency which is why the dataset is more complete. Most non-434 MHz antennas on non-Lotek receivers that are functioning are expected to detected at least _some_ pulses in a given hour bin, unless the station is at a particularly quiet site.
* Noisy antennas will have around a million pulses per day or more.&#x20;
* Noise bursts will look like a large increase in the number of pulses per day compared to days before and after. This increase will often accompany a large number of tag detections which are likely false.
* Checking for station functionality over time essentially means looking for gaps in the data, but that will only be possible in cases where data are collected consistently enough like in the example below.&#x20;

<figure><img src="../.gitbook/assets/image.png" alt=""><figcaption><p>Example data gap</p></figcaption></figure>

