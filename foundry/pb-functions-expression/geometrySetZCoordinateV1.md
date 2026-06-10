---
source_url: "https://www.palantir.com/docs/foundry/pb-functions-expression/geometrySetZCoordinateV1/"
parquet_url: "/foundry/pb-functions-expression/geometrySetZCoordinateV1/"
title: "Geometry set z-coordinate"
fetched_at: "2026-05-12T19:34:36.633Z"
---
Geometry set z-coordinate. Supported in: Batch, Faster, Streaming. Sets the z-coordinate of a geometry. If the geometry has an existing z-coordinate it will be overwritten. Expression categories: Geospatial. Declared arguments. Geometry: Geometry. Expression<Geometry> Z coordinate: Z-coordinate. Expression<Double> Output type: Geometry. Examples. Example 1: Base case. Argument values: Geometry: geometry. Z coordinate: zCoordinate. geometryzCoordinateOutput {"type":"Point","coordinates":[1.0, 2.0]} 1.0. {"type":"Point","coordinates":[1.0, 2.0, 1.0]} {"type":"Point","coordinates":[1.0, 2.0, 3.0]} 1.0. {"type":"Point","coordinates":[1.0, 2.0, 1.0]} Example 2: Null case. Argument values: Geometry: geometry. Z coordinate: zCoordinate. geometryzCoordinateOutput null. 0.0. null. {"type":"Point","coordinates":[1.0, 2.0]} null. {"type":"Point","coordinates":[1.0, 2.0]}
