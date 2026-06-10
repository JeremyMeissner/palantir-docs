---
source_url: "https://www.palantir.com/docs/foundry/quiver/card-join-materializations/"
parquet_url: "/foundry/quiver/card-join-materializations/"
title: "Join materializations"
fetched_at: "2026-05-12T19:34:37.882Z"
---
Join materializations. Performs a left, inner or right join of two materialized object data sets. Select which columns of data you wish to retain from the source and joining materializations. Optionally, add a prefix to incoming columns to avoid name collisions with existing columns, or to annotate the joined columns. This is useful if you are trying to perform a visualization or calculation using properties across linked objects in the ontology. The native object set card switch to linked object set will only perform a link traversal, resulting in the linked objects, but will not retain the original object information in the same row. Alternatively, at smaller scales (less than 50,000 objects), a join to linked objects card can be used in the transform table. Input type. Object Set, Materialization. Output type. Materialization. Usage information. FunctionalityAvailability Standard Quiver card. Supported. Transform table transform. Unsupported. See also. Join to linked objects. Switch to linked object set.
