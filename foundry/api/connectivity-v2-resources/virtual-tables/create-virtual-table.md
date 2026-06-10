---
source_url: "https://www.palantir.com/docs/foundry/api/connectivity-v2-resources/virtual-tables/create-virtual-table/"
title: "Create Virtual Table \u2022 API Reference"
---
# Create Virtual Table

## Endpoint

Creates a new [Virtual Table](/docs/foundry/data-integration/virtual-tables/) from an upstream table. The VirtualTable will be created
in the specified parent folder and can be queried through Foundry's data access APIs.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:connectivity-virtual-table-write`.

**operationId:** v2.createVirtualTable

**path:** /api/v2/connectivity/connections/{connectionRid}/virtualTables

### Operation Type

### Scopes

| name |
| --- |
| api:connectivity-virtual-table-write |

### Path Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| connectionRid | stringType | True | The Resource Identifier (RID) of a Connection (also known as a source). |

### Request

#### Body

**name:** CreateVirtualTableRequest

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| markings | listType | False |  |
| parentRid | stringType | True | The unique resource identifier (RID) of a Folder. |
| name | stringType | True | The name of a VirtualTable. |
| config | unionType | True |  |

**example:** {"markings":["18212f9a-0e63-4b79-96a0-aae04df23336"],"parentRid":"ri.compass.main.folder.c410f510-2937-420e-8ea3-8c9bcb3c1791","name":"my_table"}

### Response

#### Body

The created VirtualTable

**name:** VirtualTable

**example:** {"markings":["18212f9a-0e63-4b79-96a0-aae04df23336"],"parentRid":"ri.compass.main.folder.c410f510-2937-420e-8ea3-8c9bcb3c1791","name":"my_table","rid":"ri.foundry.main.table.c26f11c8-cdb3-4f44-9f5d-9816ea1c82da"}

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| rid | stringType | True | The Resource Identifier (RID) of a registered VirtualTable. |
| name | stringType | True | The name of a VirtualTable. |
| parentRid | stringType | True | The unique resource identifier (RID) of a Folder. |
| config | unionType | True |  |
| markings | listType | False |  |

**example:** {"markings":["18212f9a-0e63-4b79-96a0-aae04df23336"],"parentRid":"ri.compass.main.folder.c410f510-2937-420e-8ea3-8c9bcb3c1791","name":"my_table","rid":"ri.foundry.main.table.c26f11c8-cdb3-4f44-9f5d-9816ea1c82da"}

### Error Responses

| name | description |
| --- | --- |
| InvalidVirtualTableConnection | The specified connection is invalid or inaccessible. |
| VirtualTableAlreadyExists | A VirtualTable with the same name already exists in the parent folder. |
| VirtualTableRegisterFromSourcePermissionDenied | User lacks permission to use the specified connection for virtual table registration. |
| CreateVirtualTablePermissionDenied | Could not create the VirtualTable. |
| ConnectionNotFound | The given Connection could not be found. |
