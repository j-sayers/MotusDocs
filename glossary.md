# Glossary

## Detection Data

| Term       | Description                                                                                              |
| ---------- | -------------------------------------------------------------------------------------------------------- |
| Hit        | A single tag detection (equivalent to one 'burst').                                                      |
| Run        | A collections of consecutive hits. Up to 60 bursts can be missed (not detected) before a new run starts. |
| Run length | The number of detections in the run                                                                      |
| Batch      | A batch of data collected over the same receiver boot session.                                           |

## Tags

| Term                           | Description                                                                                                                                                                                                  |
| ------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Motus Tag ID                   | This is an ID unique to the physical tag and the project it sits in. If the tag was deployed twice between two projects (rare), there may be two tag IDs that exist for the same tag – one for each project. |
| Tag Deployment ID              | This is an ID defined by Motus which is unique to a single instance when a tag was attached to an individual animal. If the tag is recovered off the animal, the deployment is ended.                        |
| Manufacturer ID or mfgID       | The ID of the tag as defined by the manufactuere. This is the ID that is also digitally encoded in the radio signal transmitted by the tag.                                                                  |
| Tag ID                         | Generally refers to the Motus Tag ID within Motus documentation, but informally it can also mean the manufacturer ID.                                                                                        |
| Burst                          | A single transmission by the tag which contains its digitally encoded ID. This is equivalent to a 'hit' in the detection data.                                                                               |
| Burst Interval; or Period      | The length of time between the start of each burst.                                                                                                                                                          |
| Frequency or Nominal Frequency | The central radio frequency used to transmit the signal, usually reported in megahertz (MHz).                                                                                                                |
| Frequency offset               | The difference between the nominal frequency and the measured frequency of the tag, usually reported in kilohertz (KHz).                                                                                     |

