---
source_url: "https://www.palantir.com/docs/foundry/api/v1/ontology-resources/objects/get-object/"
parquet_url: "/foundry/api/v1/ontology-resources/objects/get-object/"
title: "Get Object"
fetched_at: "2026-05-12T19:34:37.523Z"
---
Get Object. Gets a specific object with the given primary key. Third-party applications using this endpoint via OAuth2 must request the following operation scope: api:ontologies-read. Path parameters. The unique Resource Identifier (RID) of the Ontology that contains the object. To look up your Ontology RID, please use the List ontologies endpoint or check the Ontology Manager. The API name of the object type. To find the API name, use the List object types endpoint or check the Ontology Manager. The primary key of the requested object. To look up the expected primary key for your object type, use the Get object type endpoint or the Ontology Manager. Query parameters. The properties of the object type that should be included in the response. Omit this parameter to get all the properties. Response body. Success response. A map of the property values of the object. The unique resource identifier of an object, useful for interacting with other Foundry APIs. Examples.
