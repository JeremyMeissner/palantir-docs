---
source_url: "https://www.palantir.com/docs/foundry/api/ontologies-v2-resources/object-types/list-outgoing-link-types/"
title: "List Outgoing Link Types \u2022 API Reference"
---
# List Outgoing Link Types

## Endpoint

List the outgoing links for an object type.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:ontologies-read`.

**operationId:** v2.listOutgoingLinkTypesV2

**path:** /api/v2/ontologies/{ontology}/objectTypes/{objectType}/outgoingLinkTypes

### Operation Type

### Scopes

| name |
| --- |
| api:ontologies-read |

### Path Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| ontology | stringType | True | The API name or RID of the Ontology. To find the API name or RID, use the **List Ontologies** endpoint or check the **Ontology Manager**. |
| objectType | stringType | True | The API name of the object type. To find the API name, use the **List object types** endpoint or check the **Ontology Manager** application. |

### Query Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| branch | stringType | False | The Foundry branch to load the outgoing link types from. If not specified, the default branch will be used. Branches are an experimental feature and not all workflows are supported. |
| pageSize | integerType | False | The desired size of the page to be returned. |
| pageToken | stringType | False | The page token indicates where to start paging. This should be omitted from the first page's request. To fetch the next page, clients should take the value from the `nextPageToken` field of the previous response and use it to populate the `pageToken` field of the next request. |

### Response

#### Body

Success response.

**name:** ListOutgoingLinkTypesResponseV2

**example:** {"nextPageToken":"v1.QnVpbGQgdGhlIEZ1dHVyZTogaHR0cHM6Ly93d3cucGFsYW50aXIuY29tL2NhcmVlcnMvP2xldmVyLXNvdXJjZSU1YiU1ZD1BUElEb2NzI29wZW4tcG9zaXRpb25z","data":[{"apiName":"originAirport","objectTypeApiName":"Airport","cardinality":"ONE","foreignKeyPropertyApiName":"originAirportId"}]}

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| nextPageToken | stringType | False | The page token indicates where to start paging. This should be omitted from the first page's request. To fetch the next page, clients should take the value from the `nextPageToken` field of the previous response and use it to populate the `pageToken` field of the next request. |
| data | listType | False | The list of link type sides in the current page. |

**example:** {"nextPageToken":"v1.QnVpbGQgdGhlIEZ1dHVyZTogaHR0cHM6Ly93d3cucGFsYW50aXIuY29tL2NhcmVlcnMvP2xldmVyLXNvdXJjZSU1YiU1ZD1BUElEb2NzI29wZW4tcG9zaXRpb25z","data":[{"apiName":"originAirport","objectTypeApiName":"Airport","cardinality":"ONE","foreignKeyPropertyApiName":"originAirportId"}]}
