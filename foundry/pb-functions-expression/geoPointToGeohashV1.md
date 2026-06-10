---
source_url: "https://www.palantir.com/docs/foundry/pb-functions-expression/geoPointToGeohashV1/"
title: "Convert GeoPoint to Geohash"
---
# Convert GeoPoint to Geohash

Supported in: Batch, Faster, Streaming. Converts a GeoPoint to a base32-encoded Geohash with specified precision that contains the GeoPoint. For more information on Geohash, see: https://en.wikipedia.org/wiki/Geohash . Expression categories: Geospatial. Declared arguments. GeoPoint: The GeoPoint to convert. Expression<GeoPoint> Output Geohash precision: The number of base32 characters returned in the output Geohash string. Expression<Integer> Output type: Geohash. Examples. Example 1: Base case. Argument values: GeoPoint: point. Output Geohash precision: 5. pointOutput { latitude: -20.0, longitude: 80.0, } mu2yh. { latitude: -77.0599, longitude: 38.9031, } hf79t. null. null. Example 2: Base case. Argument values: GeoPoint: point. Output Geohash precision: precision. pointprecisionOutput { latitude: -20.0, longitude: 80.0, } 5. mu2yh. { latitude: -77.0599, longitude: 38.9031, } 3. hf7. { latitude: -82.77450568, longitude: -179.55742495, } 12. 0123456789zb. { latitude: 1.0, longitude: -1.0, } 12. ebpm9npc6m9b. { latitude: 1.0, longitude: -1.0, } null. null.
