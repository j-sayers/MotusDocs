---
description: >-
  When two tags with the exact same manufacturer ID and burst rate are deployed
  simultaneously, there is no way to tell them apart.
---

# Ambiguous Tags

### What are ambiguous tags?

Motus relies on metadata to sort out when tags were deployed and therefore when to expect tags to be detected. But if two of the same tag are deployed at the same time, their identity becomes ambiguous. That is, tags with the same [<mark style="color:green;">**Manufacturer ID**</mark>](../glossary.md#tags) <mark style="color:green;">****</mark> and [<mark style="color:green;">**Burst Rate**</mark>](../glossary.md#tags) and which have an overlapping deployment period will have detections that are grouped together with an 'ambig ID': an ID unique to the specific combination of ambiguous tags.

### Why do multiples of the same tag exist?

Lotek tags encode their signal in a way that is energy efficient, but also limits the number of unique IDs to a few tens of thousands. This may seem like a lot, but we would have already exhausted this list of IDs by now if we weren't able to reissue tags. Researchers also require tags with certain burst rates based on their study design, further limiting which IDs can be used.

For this reason, we deprecate tags that have been deployed well beyond their expected lifespan ([<mark style="color:green;">**buffered lifespan**</mark>](../project-management/tag-management/tag-metadata.md#how-does-motus-know-when-tags-are-active)) and Lotek keeps track of a list of active Motus tags so they know which ones can be reissued.

However, sometimes researchers have [<mark style="color:green;">**anticipated deployments**</mark>](../project-management/tag-management/tag-metadata.md#anticipated-deployment-date) that are never completed (i.e., they anticipated they would deploy a tag, but didn't) and also don't update their metadata to indicate their tags weren't deployed on the anticipated date. This wouldn't be an issue if the tags were never deployed, but most researchers choose to hold on to their tags for subsequent field seasons at which point Lotek may have already reissued the tag to another researcher who may also choose to deploy their tag at the same time.

In the past, Motus wouldn't be aware that such tags had not been deployed, but Motus now flags anticipated deployments as 'pending' until metadata has been updated _after the_ anticipated deployment date has passed.

While this greatly reduces the possibility of ambiguous tags, mistakes can still occur and ambiguities exist in data up to and including 2022.

### How should ambiguous detection data be dealt with?

For more information on how to manage ambiguous detections, see [Chapter 5 of the Motus R Book](https://motuswts.github.io/motus/articles/05-data-cleaning.html?q=ambig#ambiguous).

{% embed url="https://motuswts.github.io/motus/articles/05-data-cleaning.html?q=ambig#ambiguous" %}
