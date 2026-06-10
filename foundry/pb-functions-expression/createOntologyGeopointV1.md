---
source_url: "https://www.palantir.com/docs/foundry/pb-functions-expression/createOntologyGeopointV1/"
title: "Convert to Ontology GeoPoint"
---
# Convert to Ontology GeoPoint

Supported in: Batch, Faster, Streaming. Convert a GeoPoint into a string that the Ontology will accept for a geo-indexed column (a geohash type column). Ontology GeoPoints are strings of the format '{lat},{lon}', where -90 <= lat <= 90 and -180 <= lon <= 180. Expression categories: Geospatial. Declared arguments. Expression: GeoPoint to convert. Expression<GeoPoint> Output type: Ontology GeoPoint. Examples. Example 1: Base case. Argument values: Expression: point. pointOutput { latitude: -20.0, longitude: 80.0, } -20.0000000,80.0000000. { latitude: 38.9031, longitude: -77.0599, } 38.9031000,-77.0599000. { latitude: 41.987654321, longitude: -99.123456789, } 41.9876543,-99.1234568. null. null.
