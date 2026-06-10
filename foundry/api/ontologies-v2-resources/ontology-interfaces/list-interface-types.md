---
source_url: "https://www.palantir.com/docs/foundry/api/ontologies-v2-resources/ontology-interfaces/list-interface-types/"
title: "List Interface Types \u2022 API Reference"
---
# List Interface Types

## Endpoint

:::callout{theme=warning title=Warning}
  This endpoint is in preview and may be modified or removed at any time.
  To use this endpoint, add `preview=true` to the request query parameters.
:::

Lists the interface types for the given Ontology.

Each page may be smaller than the requested page size. However, it is guaranteed that if there are more
results available, at least one result will be present in the response.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:ontologies-read`.

**operationId:** v2.listInterfaceTypes

**path:** /api/v2/ontologies/{ontology}/interfaceTypes

### Operation Type

### Scopes

| name |
| --- |
| api:ontologies-read |

### Path Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| ontology | stringType | True | The API name or RID of the Ontology. To find the API name or RID, use the **List Ontologies** endpoint or check the **Ontology Manager**. |

### Query Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| branch | stringType | False | The Foundry branch to list the interface types from. If not specified, the default branch will be used. Branches are an experimental feature and not all workflows are supported. |
| pageSize | integerType | False | The desired size of the page to be returned. Defaults to 500. See [page sizes](/docs/foundry/api/general/overview/paging/#page-sizes) for details. |
| pageToken | stringType | False | The page token indicates where to start paging. This should be omitted from the first page's request. To fetch the next page, clients should take the value from the `nextPageToken` field of the previous response and use it to populate the `pageToken` field of the next request. |
| preview | booleanType | False | A boolean flag that, when set to true, enables the use of beta features in preview mode. |

### Response

#### Body

Success response.

**name:** ListInterfaceTypesResponse

**example:** {"nextPageToken":"v1.QnVpbGQgdGhlIEZ1dHVyZTogaHR0cHM6Ly93d3cucGFsYW50aXIuY29tL2NhcmVlcnMvP2xldmVyLXNvdXJjZSU1YiU1ZD1BUElEb2NzI29wZW4tcG9zaXRpb25z","data":[{"apiName":"Athlete","displayName":"Athlete","description":"Good at sportsball","properties":{"name":{"rid":"com.palantir.property.d1abdbfe-0ce2-4fff-b0af-af21002c314b","apiName":"name","displayName":"Name","dataType":"string"}},"extendsInterfaces":["Human"],"rid":"ri.ontology.main.interface.bea1af8c-7d5c-4ec9-b845-8eeed6d77482"}]}

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| nextPageToken | stringType | False | The page token indicates where to start paging. This should be omitted from the first page's request. To fetch the next page, clients should take the value from the `nextPageToken` field of the previous response and use it to populate the `pageToken` field of the next request. |
| data | listType | False |  |

**example:** {"nextPageToken":"v1.QnVpbGQgdGhlIEZ1dHVyZTogaHR0cHM6Ly93d3cucGFsYW50aXIuY29tL2NhcmVlcnMvP2xldmVyLXNvdXJjZSU1YiU1ZD1BUElEb2NzI29wZW4tcG9zaXRpb25z","data":[{"apiName":"Athlete","displayName":"Athlete","description":"Good at sportsball","properties":{"name":{"rid":"com.palantir.property.d1abdbfe-0ce2-4fff-b0af-af21002c314b","apiName":"name","displayName":"Name","dataType":"string"}},"extendsInterfaces":["Human"],"rid":"ri.ontology.main.interface.bea1af8c-7d5c-4ec9-b845-8eeed6d77482"}]}
