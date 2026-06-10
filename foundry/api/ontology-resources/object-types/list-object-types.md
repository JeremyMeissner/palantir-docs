---
source_url: "https://www.palantir.com/docs/foundry/api/ontology-resources/object-types/list-object-types/"
title: "List Object Types \u2022 API Reference"
---
# List Object Types

## Endpoint

Lists the object types for the given Ontology.

Each page may be smaller or larger than the requested page size. However, it is guaranteed that if there are
more results available, at least one result will be present in the
response.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:ontologies-read`.

**operationId:** v1.listObjectTypes

**path:** /api/v1/ontologies/{ontologyRid}/objectTypes

### Operation Type

### Scopes

| name |
| --- |
| api:ontologies-read |

### Path Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| ontologyRid | stringType | True | The unique Resource Identifier (RID) of the Ontology that contains the object types. To look up your Ontology RID, please use the **List ontologies** endpoint or check the **Ontology Manager**. |

### Query Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| pageSize | integerType | False | The desired size of the page to be returned. Defaults to 500. See [page sizes](/docs/foundry/api/general/overview/paging/#page-sizes) for details. |
| pageToken | stringType | False | The page token indicates where to start paging. This should be omitted from the first page's request. To fetch the next page, clients should take the value from the `nextPageToken` field of the previous response and use it to populate the `pageToken` field of the next request. |

### Response

#### Body

Success response.

**name:** ListObjectTypesResponse

**example:** {"nextPageToken":"v1.QnVpbGQgdGhlIEZ1dHVyZTogaHR0cHM6Ly93d3cucGFsYW50aXIuY29tL2NhcmVlcnMvP2xldmVyLXNvdXJjZSU1YiU1ZD1BUElEb2NzI29wZW4tcG9zaXRpb25z","data":[{"apiName":"employee","description":"A full-time or part-time employee of our firm","primaryKey":["employeeId"],"properties":{"employeeId":{"baseType":"Integer"},"fullName":{"baseType":"String"},"office":{"description":"The unique ID of the employee's primary assigned office","baseType":"String"},"startDate":{"description":"The date the employee was hired (most recently, if they were re-hired)","baseType":"Date"}},"rid":"ri.ontology.main.object-type.401ac022-89eb-4591-8b7e-0a912b9efb44"},{"apiName":"office","description":"A physical location (not including rented co-working spaces)","primaryKey":["officeId"],"properties":{"officeId":{"baseType":"String"},"address":{"description":"The office's physical address (not necessarily shipping address)","baseType":"String"},"capacity":{"description":"The maximum seated-at-desk capacity of the office (maximum fire-safe capacity may be higher)","baseType":"Integer"}},"rid":"ri.ontology.main.object-type.9a0e4409-9b50-499f-a637-a3b8334060d9"}]}

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| nextPageToken | stringType | False | The page token indicates where to start paging. This should be omitted from the first page's request. To fetch the next page, clients should take the value from the `nextPageToken` field of the previous response and use it to populate the `pageToken` field of the next request. |
| data | listType | False | The list of object types in the current page. |

**example:** {"nextPageToken":"v1.QnVpbGQgdGhlIEZ1dHVyZTogaHR0cHM6Ly93d3cucGFsYW50aXIuY29tL2NhcmVlcnMvP2xldmVyLXNvdXJjZSU1YiU1ZD1BUElEb2NzI29wZW4tcG9zaXRpb25z","data":[{"apiName":"employee","description":"A full-time or part-time employee of our firm","primaryKey":["employeeId"],"properties":{"employeeId":{"baseType":"Integer"},"fullName":{"baseType":"String"},"office":{"description":"The unique ID of the employee's primary assigned office","baseType":"String"},"startDate":{"description":"The date the employee was hired (most recently, if they were re-hired)","baseType":"Date"}},"rid":"ri.ontology.main.object-type.401ac022-89eb-4591-8b7e-0a912b9efb44"},{"apiName":"office","description":"A physical location (not including rented co-working spaces)","primaryKey":["officeId"],"properties":{"officeId":{"baseType":"String"},"address":{"description":"The office's physical address (not necessarily shipping address)","baseType":"String"},"capacity":{"description":"The maximum seated-at-desk capacity of the office (maximum fire-safe capacity may be higher)","baseType":"Integer"}},"rid":"ri.ontology.main.object-type.9a0e4409-9b50-499f-a637-a3b8334060d9"}]}
