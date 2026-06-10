---
source_url: "https://www.palantir.com/docs/foundry/api/v2/ontologies-v2-resources/time-series-value-bank-properties/get-latest-value/"
title: "Get Latest Value"
---
# Get Latest Value

Get the latest value of a property backed by a timeseries. If a specific geotime series integration has both a history and a live integration, we will give precedence to the live integration. Third-party applications using this endpoint via OAuth2 must request the following operation scope: api:ontologies-read. Path parameters. The API name or RID of the Ontology. To find the API name or RID, use the List Ontologies endpoint or check the Ontology Manager. The API name of the object type. To find the API name, use the List object types endpoint or check the Ontology Manager. The primary key of the object with the timeseries property. The API name of the timeseries property. To find the API name for your property value bank property, check the Ontology Manager or use the Get object type endpoint. Query parameters. The package rid of the generated SDK. The version of the generated SDK. Response body. Success response. An ISO 8601 timestamp. An object which is either an enum String, double number, or a geopoint. Examples.
