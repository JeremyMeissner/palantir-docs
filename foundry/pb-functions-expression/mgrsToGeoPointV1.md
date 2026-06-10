---
source_url: "https://www.palantir.com/docs/foundry/pb-functions-expression/mgrsToGeoPointV1/"
title: "Convert MGRS to GeoPoint"
---
# Convert MGRS to GeoPoint

Supported in: Batch, Faster, Streaming. Converts a MGRS (military grid reference system) coordinate into a GeoPoint following the WGS84 coordinate system (which is EPSG:4326). Expression categories: Geospatial. Declared arguments. Expression: MGRS (military grid reference system) coordinate to convert. Expression<MGRS> Output type: GeoPoint. Examples. Example 1: Base case. Argument values: Expression: mgrs. mgrsOutput ZAF0193788990. { latitude: 88.99999659707431, longitude: 0.9996456505181999, } Example 2: Base case. Argument values: Expression: mgrs. mgrsOutput 4Q FJ 12345 67890. { latitude: 21.409796671597924, longitude: -157.91608117421092, } 4Q FJ 1 6. { latitude: 21.338665624760598, longitude: -157.93921670599434, } 4Q FJ 123 678. { latitude: 21.40898645576642, longitude: -157.91652127483704, } Example 3: Null case. Argument values: Expression: mgrs. mgrsOutput null. null.
