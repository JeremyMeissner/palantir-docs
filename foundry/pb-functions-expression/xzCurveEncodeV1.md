---
source_url: "https://www.palantir.com/docs/foundry/pb-functions-expression/xzCurveEncodeV1/"
parquet_url: "/foundry/pb-functions-expression/xzCurveEncodeV1/"
title: "Get XZ curve index of an envelope"
fetched_at: "2026-05-12T19:34:36.583Z"
---
Get XZ curve index of an envelope. Supported in: Batch, Streaming. Encodes the envelope in an XZ curve. Expression categories: Geospatial. Declared arguments. Curve preset: Specifies the curve preset to use, higher resolution curves are more expensive to query but produce fewer false positives. Enum<LonLat10km, LonLat150km, LonLat1km> Envelope: Geometry envelope to index with longitude mapped to x, and latitude mapped to y. Expression<LatLonBoundingBox> Output type: Long. Examples. Example 1: Base case. Argument values: Curve preset: LON_LAT_10KM. Envelope: envelope. envelopeOutput { maxLat -> 2.0, maxLon -> 3.0, minLat -> 0.0, minLon -> 1.0, } 16777222. { maxLat -> 2.0, maxLon -> 3.0, minLat -> null, minLon -> 1.0, } null.
