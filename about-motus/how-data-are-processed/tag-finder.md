# Tag Finder

Tag finder is a complex algorithm used to decode IDs of Lotek tags from the raw data collected by SensorGnomes and SensorStations. It was originally developed by John Brustowski and Phil Taylor at Acadia University.

This chapter is intended to provided an overview of how tag finder works and where issues may arise. For a complete, in depth look at the algorithm and its code, see [**the find\_tags github repository**](https://github.com/sensorgnome-org/find\_tags).

{% hint style="info" %}
This chapter describes the algorithm used to decode the IDs of Lotek Tags. For  information on how CTT tag data are processed, see [**How Data are Processed.**](../how-data-are-processed.md#ctt-detection-data)****
{% endhint %}

## Overview

Tag finder takes in a series of time-stamped radio pulses and decodes them by matching them to a list of known Motus Tag IDs. A Lotek tag ID consists of a "burst" of four pulses which are precisely spaced apart such that every tag ID has _three unique pulse gaps._ Motus extends these IDs by using the interval between bursts as a _fourth unique pulse gap._ Tag finder is capable of decoding IDs of tags that have overlapping bursts using a technique described below.

## How it works

Tag finder uses a computer science concept called _Deterministic Finite Automata (DFAs)_ to associate a series of time-stamped pulses with known Motus Tag IDs. For any given set of pulses, it looks at the first pulse gap and creates a list of 'tag candidates' which the gap could be associated with. It then continues to the next pulse gaps one at a time, narrowing down the list of candidates until just one candidate is left - those pulses are then 'reserved' for that tag and cannot be associated with another tag. During this process, many pulses will be skipped if the gaps don't match any known tag IDs. The first skipped pulse will become the starting point for the next DFA, making it possible to separate out pulses from  overlapping bursts.

Tag finder must identify at least _two bursts_ in order to associate pulses with a tag candidate, but often the second burst will be missed due to poor signal. To maximize the possibility of getting a Motus Tag ID, tag finder will continue searching for another burst which matches the candidate tag(s) for up to 20 skipped bursts.

The list of tag candidates is based on all Motus Tag IDs that known to be deployed when the pulses occurred. This means it's not possible for _tag finder_ to identify tags if they aren't registered to Motus with a deployment.&#x20;

## **Parameters**

There are a series of parameters that tag finder uses to associate a pulse gap with a Motus Tag ID. It uses empirically-based cutoffs for associating pulses with a tag as well as parameters of the tag that were measured when it was first registered to Motus.&#x20;

For pulses to be grouped together, they must share a similar signal strength, frequency offset, and the pulse gaps must match the expected pulse gaps of the tag within 2 milliseconds. Burst intervals are allowed to vary by up to 4 milliseconds and it will also increase this variation by 1 millisecond for every burst that is skipped.&#x20;

****[**See our documentation on the parameters for tag finder here**](https://github.com/MotusDev/Motus-TO-DO/issues/465).
