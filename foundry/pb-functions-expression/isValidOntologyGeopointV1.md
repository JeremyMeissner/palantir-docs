---
source_url: "https://www.palantir.com/docs/foundry/pb-functions-expression/isValidOntologyGeopointV1/"
title: "Is valid Ontology GeoPoint"
---
# Is valid Ontology GeoPoint

Supported in: Batch, Faster, Streaming. Returns true if the input is a valid Ontology GeoPoint. Ontology GeoPoints are strings of the format '{lat},{lon}', where -90 <= lat <= 90 and -180 <= lon <= 180. Expression categories: Geospatial. Declared arguments. Expression: String to test. Expression<String> Output type: Boolean. Examples. Example 1: Base case. Argument values: Expression: geopoint. geopointOutput -35.307428203,149.122686883. true. 149.122686883,-35.307428203. false. 10.0, 20.0. true. 10.0, 20.0. true. not a GeoPoint. false. null. false. (10.0,20.0). false.
