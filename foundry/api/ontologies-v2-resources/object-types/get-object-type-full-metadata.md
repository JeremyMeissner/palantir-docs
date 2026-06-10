---
source_url: "https://www.palantir.com/docs/foundry/api/ontologies-v2-resources/object-types/get-object-type-full-metadata/"
title: "Get Object Type Full Metadata \u2022 API Reference"
---
# Get Object Type Full Metadata

## Endpoint

:::callout{theme=warning title=Warning}
  This endpoint is in preview and may be modified or removed at any time.
  To use this endpoint, add `preview=true` to the request query parameters.
:::

Gets the full metadata for a specific object type with the given API name.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:ontologies-read`.

**operationId:** v2.getObjectTypeFullMetadata

**path:** /api/v2/ontologies/{ontology}/objectTypes/{objectType}/fullMetadata

### Operation Type

### Scopes

| name |
| --- |
| api:ontologies-read |

### Path Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| ontology | stringType | True | The API name or RID of the Ontology. To find the API name or RID, use the **List Ontologies** endpoint or check the **Ontology Manager**. |
| objectType | stringType | True | The API name of the object type. To find the API name, use the **List object types** endpoint or check the **Ontology Manager**. |

### Query Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| preview | booleanType | False | A boolean flag that, when set to true, enables the use of beta features in preview mode. |
| sdkPackageRid | stringType | False | The package rid of the generated SDK. |
| sdkVersion | stringType | False | The version of the generated SDK. |
| branch | stringType | False | The Foundry branch to load the action type definition from. If not specified, the default branch will be used. Branches are an experimental feature and not all workflows are supported. |

### Response

#### Body

Success response.

**name:** ObjectTypeFullMetadata

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| objectType | objectType | True | Represents an object type in the Ontology. |
| linkTypes | listType | False |  |
| implementsInterfaces | listType | False | A list of interfaces that this object type implements. |
| implementsInterfaces2 | mapType | False | A list of interfaces that this object type implements and how it implements them. |
| sharedPropertyTypeMapping | mapType | False | A map from shared property type API name to backing local property API name for the shared property types  present on this object type. |
