---
source_url: "https://www.palantir.com/docs/foundry/pb-functions-expression/constructGeoPointV1/"
title: "Create GeoPoint"
---
# Create GeoPoint

Supported in: Batch, Faster, Streaming. Creates a GeoPoint column from a latitude and longitude column. Validates that the latitude parameter is between -90 and 90, inclusive, and that the longitude parameter is between -180 and 180, inclusive; if not, returns a null value. Expression categories: Geospatial. Declared arguments. Latitude: Latitude column. Expression<Double> Longitude: Longitude column. Expression<Double> Output type: GeoPoint. Examples. Example 1: Base case. Argument values: Latitude: lat. Longitude: lon. latlonOutput 32.0. 58.0. { latitude -> 32.0, longitude -> 58.0, } 320.0. 58.0. null. Example 2: Null case. Argument values: Latitude: lat. Longitude: lon. latlonOutput null. null. null. null. 58.0. null. 32.0. null. null. NaN. 30.0. null.
