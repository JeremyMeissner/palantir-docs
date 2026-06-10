---
source_url: "https://www.palantir.com/docs/foundry/pb-functions-expression/h3ToGeoPointV1/"
parquet_url: "/foundry/pb-functions-expression/h3ToGeoPointV1/"
title: "Convert H3 index to GeoPoint"
fetched_at: "2026-05-12T19:34:36.617Z"
---
Convert H3 index to GeoPoint. Supported in: Batch, Faster, Streaming. Convert an H3 index into the GeoPoint representing the center of the corresponding H3 hexagon. Expression categories: Geospatial. Declared arguments. Expression: The H3 index to convert to a GeoPoint. Expression<H3 Index> Output type: GeoPoint. Examples. Example 1: Base case. Argument values: Expression: h3. h3Output 85aa614bfffffff. { latitude: -20.040068721942628, longitude: 79.95021089904623, } 852aa84ffffffff. { latitude: 38.926035503721714, longitude: -77.1525762709701, } Example 2: Null case. Argument values: Expression: h3. h3Output null. null. Example 3: Edge case. Argument values: Expression: h3. h3Output h3. null.
