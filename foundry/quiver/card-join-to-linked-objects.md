---
source_url: "https://www.palantir.com/docs/foundry/quiver/card-join-to-linked-objects/"
parquet_url: "/foundry/quiver/card-join-to-linked-objects/"
title: "Join to linked objects"
fetched_at: "2026-05-12T19:34:37.925Z"
---
Join to linked objects. Perform an inner join with linked objects using a link relation. This is useful if you are trying to perform a visualization or calculation using properties across linked objects in the ontology. The native object set card switch to linked object set will only perform a link traversal, resulting in the linked objects, but will not retain the original object information in the same row. Alternatively, if your set is larger than 50,000 rows and cannot use the transform table, use a join materializations card to join objects across links at scale. Input type. Transform table. Output type. Transform table. Usage information. FunctionalityAvailability Standard Quiver card. Unsupported. Transform table transform. Supported. See also. Join materializations. Switch to linked object set.
