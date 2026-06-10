---
source_url: "https://www.palantir.com/docs/foundry/pb-functions-expression/haversineV1/"
title: "Calculate haversine distance"
---
# Calculate haversine distance

Supported in: Batch, Faster, Streaming. Calculates the haversine distance between two latitude and longitude point pairs in meters. Expression categories: Geospatial. Declared arguments. Point a: Longitude and latitude for point b. Expression<GeoPoint> Point b: Longitude and latitude for point a. Expression<GeoPoint> Output type: Double. Examples. Example 1: Base case. Argument values: Point a: point_a. Point b: point_b. point_apoint_bOutput { latitude: 41.507483, longitude: -99.436554, } { latitude: 38.504048, longitude: -98.315949, } 347328.82778977347. { latitude: 22.308919, longitude: 113.914603, } { latitude: -33.946111, longitude: 151.177222, } 7393894.00134442.
