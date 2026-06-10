---
source_url: "https://www.palantir.com/docs/foundry/pb-functions-expression/linestringToPolygonV1/"
parquet_url: "/foundry/pb-functions-expression/linestringToPolygonV1/"
title: "Convert linestring to polygon"
fetched_at: "2026-05-12T19:34:36.575Z"
---
Convert linestring to polygon. Supported in: Batch, Faster, Streaming. Convert a linestring geometry to a polygon geometry. This expression assumes the linestring geometry is closed. If not, the expression will return null. Expression categories: Geospatial. Declared arguments. Expression: A valid linestring geometry. Expression<Geometry> Output type: Geometry. Examples. Example 1: Base case. Argument values: Expression: polygon_points. polygon_pointsOutput {"type":"LineString","coordinates":[[-77.49,38.01],[-77.47,38.15],[-77.19,38.14],[-77.49,38.01]]} {"type":"Polygon","coordinates":[[[-77.49,38.01],[-77.47,38.15],[-77.19,38.14],[-77.49,38.01]]]} Example 2: Null case. Argument values: Expression: polygon_points. polygon_pointsOutput null. null. {"type":"LineString","coordinates":[[-77.49,38.01],[-77.19,38.14],[-77.49,38.01]]} null. {"type":"LineString","coordinates":[[-77.49,38.01],[-77.19,38.14]]} null. {"type":"LineString","coordinates":[[-77.49,38.01]]} null. {"type":"Polygon","coordinates":[[[-77.49,38.01],[-77.47,38.15],[-77.19,38.14],[-77.49,38.01]]]} null.
