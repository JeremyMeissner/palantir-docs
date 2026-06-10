---
source_url: "https://www.palantir.com/docs/foundry/pb-functions-expression/h3IndexExpressionV1/"
title: "Get H3 index"
---
# Get H3 index

Supported in: Batch, Faster, Streaming. Convert GeoPoint to H3 index at given resolution. Returns null for resolution <0 or >15. Expression categories: Geospatial. Declared arguments. GeoPoint: GeoPoint (lon,lat) to convert to H3 index. Expression<GeoPoint> Resolution: H3 grid resolution between 0 and 15 (inclusive). Expression<Byte | Integer | Long | Short> Output type: H3 Index. Examples. Example 1: Base case. Argument values: GeoPoint: point. Resolution: 5. pointOutput { latitude: -20.0, longitude: 80.0, } 85aa614bfffffff. { latitude: 38.9031, longitude: -77.0599, } 852aa84ffffffff. Example 2: Base case. Argument values: GeoPoint: constructGeoPoint( latitude: 80.0, longitude: -20.0, ). Resolution: 5. Output: 8507b297fffffff.
