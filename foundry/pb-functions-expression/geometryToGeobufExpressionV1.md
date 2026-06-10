---
source_url: "https://www.palantir.com/docs/foundry/pb-functions-expression/geometryToGeobufExpressionV1/"
title: "Encode GeoJSON as Geobuf"
---
# Encode GeoJSON as Geobuf

Supported in: Batch, Faster, Streaming. Encodes GeoJSON geometry as Geobuf. Expression categories: Geospatial. Declared arguments. Geometry: Geometry to convert to Geobuf. Expression<Geometry> optional Dimensions: Number of dimensions per coordinate encoded in the Geobuf. Expression<Integer> optional Precision: Number of preserved decimals after the decimal point. Expression<Integer> Output type: Geobuf. Examples. Example 1: Base case. Argument values: Geometry: geojson. Dimensions: null. Precision: null. geojsonOutput {"type":"Point","coordinates": [32.0, 58.0]} MgwIABoIgKDCHoCKqDc= null. null. {"type":"Point","coordinates": [-73.989015, 40.753206]} MgwIABoIre7HRuzg7iY=
