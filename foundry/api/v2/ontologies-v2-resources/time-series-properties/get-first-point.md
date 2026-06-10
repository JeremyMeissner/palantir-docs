---
source_url: "https://www.palantir.com/docs/foundry/api/v2/ontologies-v2-resources/time-series-properties/get-first-point/"
title: "Get First Point"
---
# Get First Point

Get the first point of a time series property. Third-party applications using this endpoint via OAuth2 must request the following operation scope: api:ontologies-read. Path parameters. The API name or RID of the Ontology. To find the API name or RID, use the List Ontologies endpoint or check the Ontology Manager. The API name of the object type. To find the API name, use the List object types endpoint or check the Ontology Manager. The primary key of the object with the time series property. The API name of the time series property. To find the API name for your time series property, check the Ontology Manager or use the Get object type endpoint. Query parameters. The package rid of the generated SDK. The version of the generated SDK. Response body. Success response. An ISO 8601 timestamp. An object which is either an enum String or a double number. Examples.
