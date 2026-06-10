---
source_url: "https://www.palantir.com/docs/foundry/api/v2/ontologies-v2-resources/time-series-value-bank-properties/stream-values/"
title: "Stream Values"
---
# Stream Values

Stream all of the points of a time series property (this includes geotime series references). Third-party applications using this endpoint via OAuth2 must request the following operation scope: api:ontologies-read. Path parameters. The API name or RID of the Ontology. To find the API name or RID, use the List Ontologies endpoint or check the Ontology Manager. The API name of the object type. To find the API name, use the List object types endpoint or check the Ontology Manager. The primary key of the object with the time series property. The API name of the time series backed property. To find the API name, check the Ontology Manager or use the Get object type endpoint. Query parameters. The package rid of the generated SDK. The version of the generated SDK. Request body. An absolute or relative range for a time series query. Response body. Success response. Examples.
