---
source_url: "https://www.palantir.com/docs/foundry/pb-functions-expression/geoPointToMgrsV1/"
title: "Convert GeoPoint to MGRS"
---
# Convert GeoPoint to MGRS

Supported in: Batch, Faster, Streaming. Converts a GeoPoint following the WGS84 coordinate system (which is EPSG:4326) to a MGRS (military grid reference system) coordinate. The output MGRS will follow a space-delimited format with 5 digits of precision. Expression categories: Geospatial. Declared arguments. Expression: GeoPoint to convert. Expression<GeoPoint> Output type: MGRS. Examples. Example 1: Base case. Argument values: Expression: geoPoint. geoPointOutput { latitude -> 88.99999659707431, longitude -> 0.9996456505181999, } Z AF 01937 88990. Example 2: Base case. Argument values: Expression: geoPoint. geoPointOutput { latitude -> 21.409796671597924, longitude -> -157.91608117421092, } 4Q FJ 12345 67889. { latitude -> 21.338665624760598, longitude -> -157.93921670599434, } 4Q FJ 10000 59999. { latitude -> 21.40898645576642, longitude -> -157.91652127483704, } 4Q FJ 12300 67799. Example 3: Null case. Argument values: Expression: geoPoint. geoPointOutput null. null.
