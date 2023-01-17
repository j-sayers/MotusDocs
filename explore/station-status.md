# Station Status

This chapter outlines ways you can use the data dashboard to explore the status of a Motus station.

The status of a Motus station refers to various parameters which help us diagnose its ability to detect Motus tags. There are many reasons you may want to check on the status of a Motus station. For one, it's an important part of regular station maintenance for collaborators who manage part of the Motus network. It can also be a key tool for identifying the source of data gaps.

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

* GPS are normally stored at least once an hour so they can be a helpful way to identify when a station was powered on and logging data. However, GPS hits are not collected by all receivers equally; some stations may present frequent gaps in these data. In addition, SensorGnomes frequently have malfunctioning GPS units which make them unreliable. Many Lotek receivers will not collect any GPS hits.
* Antenna activity can be useful for identifying issues with specific antennas and is a reflection of environmental noise. The amount of noise detected depends largely on the frequency, location, and time of day. Activity on 434 MHz antennas (with the 'L' prefix) or on Lotek receivers are actually showing instances where false detections have occurred so this dataset is typically fairly sparse. On the other hand, activity on all other antenna frequencies are displaying raw pulses on that frequency which occurs far more frequently, usually hundreds to thousands of times hourly. &#x20;
* Noisy antennas will collect millions of pulses a day, whereas ones at quiet sites will collect no pulses for several hours or days at a time
* Noise bursts will look like a large increase in the number of pulses per day compared to days before and after. This increase will often accompany a large number of tag detections which are likely false.
* Checking for station functionality over time essentially means looking for gaps in the data, but that will only be possible in cases where data are collected consistently enough like in the example below.&#x20;

<figure><img src="../.gitbook/assets/image.png" alt=""><figcaption><p>Example data gap</p></figcaption></figure>

