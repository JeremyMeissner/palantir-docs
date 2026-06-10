---
source_url: "https://www.palantir.com/docs/foundry/api/v2/ontologies-v2-resources/time-series-properties/stream-points/"
parquet_url: "/foundry/api/v2/ontologies-v2-resources/time-series-properties/stream-points/"
title: "Stream Points"
fetched_at: "2026-05-12T19:34:37.624Z"
---
Stream Points. Stream all of the points of a time series property. Third-party applications using this endpoint via OAuth2 must request the following operation scope: api:ontologies-read. Path parameters. The API name or RID of the Ontology. To find the API name or RID, use the List Ontologies endpoint or check the Ontology Manager. The API name of the object type. To find the API name, use the List object types endpoint or check the Ontology Manager. The primary key of the object with the time series property. The API name of the time series property. To find the API name for your time series property, check the Ontology Manager or use the Get object type endpoint. Query parameters. The package rid of the generated SDK. The version of the generated SDK. The output format to serialize the output binary stream in. Default is JSON. ARROW is more efficient than JSON at streaming a large sized response. Enum values: JSON, ARROW. Request body. An absolute or relative range for a time series query. Response body. Success response. Examples.
