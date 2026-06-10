---
source_url: "https://www.palantir.com/docs/foundry/api/ontology-resources/action-types/list-action-types/"
title: "List Action Types \u2022 API Reference"
---
# List Action Types

## Endpoint

Lists the action types for the given Ontology.

Each page may be smaller than the requested page size. However, it is guaranteed that if there are more
results available, at least one result will be present in the response.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:ontologies-read`.

**operationId:** v1.listActionTypes

**path:** /api/v1/ontologies/{ontologyRid}/actionTypes

### Operation Type

### Scopes

| name |
| --- |
| api:ontologies-read |

### Path Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| ontologyRid | stringType | True | The unique Resource Identifier (RID) of the Ontology that contains the action types. To look up your Ontology RID, please use the **List ontologies** endpoint or check the **Ontology Manager**. |

### Query Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| pageSize | integerType | False | The desired size of the page to be returned. Defaults to 500. See [page sizes](/docs/foundry/api/general/overview/paging/#page-sizes) for details. |
| pageToken | stringType | False | The page token indicates where to start paging. This should be omitted from the first page's request. To fetch the next page, clients should take the value from the `nextPageToken` field of the previous response and use it to populate the `pageToken` field of the next request. |

### Response

#### Body

Success response.

**name:** ListActionTypesResponse

**example:** {"nextPageToken":"v1.QnVpbGQgdGhlIEZ1dHVyZTogaHR0cHM6Ly93d3cucGFsYW50aXIuY29tL2NhcmVlcnMvP2xldmVyLXNvdXJjZSU1YiU1ZD1BUElEb2NzI29wZW4tcG9zaXRpb25z","data":[{"apiName":"promote-employee","description":"Update an employee's title and compensation","parameters":{"employeeId":{"baseType":"Integer"},"newTitle":{"baseType":"String"},"newCompensation":{"baseType":"Decimal"}},"rid":"ri.ontology.main.action-type.7ed72754-7491-428a-bb18-4d7296eb2167"},{"apiName":"move-office","description":"Update an office's physical location","parameters":{"officeId":{"baseType":"String"},"newAddress":{"description":"The office's new physical address (not necessarily shipping address)","baseType":"String"},"newCapacity":{"description":"The maximum seated-at-desk capacity of the new office (maximum fire-safe capacity may be higher)","baseType":"Integer"}},"rid":"ri.ontology.main.action-type.9f84017d-cf17-4fa8-84c3-8e01e5d594f2"}]}

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| nextPageToken | stringType | False | The page token indicates where to start paging. This should be omitted from the first page's request. To fetch the next page, clients should take the value from the `nextPageToken` field of the previous response and use it to populate the `pageToken` field of the next request. |
| data | listType | False |  |

**example:** {"nextPageToken":"v1.QnVpbGQgdGhlIEZ1dHVyZTogaHR0cHM6Ly93d3cucGFsYW50aXIuY29tL2NhcmVlcnMvP2xldmVyLXNvdXJjZSU1YiU1ZD1BUElEb2NzI29wZW4tcG9zaXRpb25z","data":[{"apiName":"promote-employee","description":"Update an employee's title and compensation","parameters":{"employeeId":{"baseType":"Integer"},"newTitle":{"baseType":"String"},"newCompensation":{"baseType":"Decimal"}},"rid":"ri.ontology.main.action-type.7ed72754-7491-428a-bb18-4d7296eb2167"},{"apiName":"move-office","description":"Update an office's physical location","parameters":{"officeId":{"baseType":"String"},"newAddress":{"description":"The office's new physical address (not necessarily shipping address)","baseType":"String"},"newCapacity":{"description":"The maximum seated-at-desk capacity of the new office (maximum fire-safe capacity may be higher)","baseType":"Integer"}},"rid":"ri.ontology.main.action-type.9f84017d-cf17-4fa8-84c3-8e01e5d594f2"}]}
