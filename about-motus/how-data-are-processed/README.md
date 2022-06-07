# How Data are Processed

{% hint style="danger" %}
This section is in development
{% endhint %}

## Data Processing Pipeline

Data are processed differently depending on the type of receiver and tag. Data received from Lotek tags are processed on the Motus server where it matches the ID and burst intervals to known tags within the system. Similarly, CTT tag data are processed on CTT's servers where it can be validated agains its own list of tag IDs which have been manufactured. Due to these differences in data processing, data uploaded to Motus - either manual or automated - need to be routed to the correct server based on its contents.

The three diagrams below outline the data processing pipelines for [**the three types of receivers** ](../../stations/station-equipment/receivers.md)used within the Motus network.

![SesnorGnome Data Processing Pipeline](<../../.gitbook/assets/SensorGnome Data Processing Pipeline Diagram.png>)

![CTT SensorStation Data Processing Pipeline](<../../.gitbook/assets/CTT SensorStation Data Processing Pipeline Diagram.png>)

![Lotek SRX Data Processing Pipeline](<../../.gitbook/assets/Lotek SRX Data Processing Pipeline Diagram.png>)
