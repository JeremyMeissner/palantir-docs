---
source_url: "https://www.palantir.com/docs/foundry/pb-functions-expression/groupedLatLonBoundingBoxV1/"
parquet_url: "/foundry/pb-functions-expression/groupedLatLonBoundingBoxV1/"
title: "Grouped latitude/longitude bounding box"
fetched_at: "2026-05-12T19:34:36.762Z"
---
Grouped latitude/longitude bounding box. Supported in: Batch. Returns a struct containing the entire bounding box of all valid geometries in the given column. Invalid geometries are treated as null and ignored. Expression categories: Geospatial. Declared arguments. Expression: Column of geometries to compute the entire bounding box of. Expression<Geometry> Output type: LatLonBoundingBox. Examples. Example 1: Base case. Argument values: Expression: geometry. Given input table: geometry {"type":"LineString","coordinates":[[1,0],[0,8.4]]} {"type":"Point","coordinates":[125.6, -92.3]} {"type":"Polygon","coordinates":[[[0,0],[1,6.3],[-6,1],[0,0]]]} Outputs: { maxLat -> 8.4, maxLon -> 125.6, minLat -> -92.3, minLon -> -6.0, } Example 2: Null case. Argument values: Expression: geometry. Given input table: geometry null. Outputs: null. Example 3: Edge case. Argument values: Expression: geometry. Given input table: geometry Invalid GeoJSON. {"type":"LineString","coordinates":[[2,0],[0,4.8]]} Outputs: { maxLat -> 4.8, maxLon -> 2.0, minLat -> 0.0, minLon -> 0.0, }
