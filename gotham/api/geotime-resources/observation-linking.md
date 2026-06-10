---
source_url: "https://www.palantir.com/docs/gotham/api/geotime-resources/observation-linking/"
title: "Observation linking basics \u2022 API Reference"
---
Adding links to tracks is a way of noting that the two items have a relationship. Observation links are always
bi-directional unlike with object links. Object linkage is a related but separate concept and you can read more about it 
[here](/docs/gotham/api/revdb-resources/objects/create-object-link/).

We can use links on tracks in the following ways:
- To denote a relationship between a Track and an Object, in which case the link likely indicates that the Track
  is just a set of geotemporal locations for that object. For example, if Airplane A-238-A was flown to London from
  New York, the Track of that trip could be linked to the plane object.
- To denote a relationship between two Tracks, where the link likely indicates that the tracks come from the same 
  Object or bear non-trivial similarities. For example, if two tracks have the same route from New York to London in a 
  period of two days, but we aren't certain they're produced by the same plane, we can link the tracks.

Unlike with [object-resolution](/docs/gotham/api/revdb-resources/resolution/resolution-basics/), linking Tracks does not eliminate the individual items, and does not create
a third item. The Tracks remain separate. Similarly, if Track A and Track B are linked, and we add a link from
Track B to Track C, the link will not be transitively applied to Track A. 

Unlinking is supported in cases where applying this relationship is no longer desired. Like linking, unlinking does not
transitively apply to other Tracks. That is if Track A and Track B are both linked to Track C, unlinking Track B from
Track C will not affect the link from Track A to Track C.
