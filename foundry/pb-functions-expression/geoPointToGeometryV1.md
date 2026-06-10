---
source_url: "https://www.palantir.com/docs/foundry/pb-functions-expression/geoPointToGeometryV1/"
parquet_url: "/foundry/pb-functions-expression/geoPointToGeometryV1/"
title: "Convert GeoPoint to geometry"
fetched_at: "2026-05-12T19:34:36.783Z"
---
Convert GeoPoint to geometry. Supported in: Batch, Faster, Streaming. Convert GeoPoint to a GeoJSON of type point. Expression categories: Geospatial. Declared arguments. Expression: A valid GeoPoint. Expression<GeoPoint> Output type: Geometry. Examples. Example 1: Base case. Argument values: Expression: geoPoint. geoPointOutput { latitude -> 58.0, longitude -> 32.0, } {"type":"Point","coordinates": [32.0, 58.0]} null. null. { latitude -> 40.753206, longitude -> -73.989015, } {"type":"Point","coordinates": [-73.989015, 40.753206]}
