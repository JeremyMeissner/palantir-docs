---
source_url: "https://www.palantir.com/docs/foundry/api/filesystem-v2-resources/folders/list-children-of-folder/"
title: "List Children Of Folder \u2022 API Reference"
---
# List Children Of Folder

## Endpoint

List all child Resources of the Folder.

This is a paged endpoint. The page size will be limited to 2,000 results per page. If no page size is
provided, this page size will also be used as the default.

**operationId:** v2.listChildrenOfFolder

**path:** /api/v2/filesystem/folders/{folderRid}/children

### Operation Type

### Path Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| folderRid | stringType | True | The unique resource identifier (RID) of a Folder. |

### Query Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| pageSize | integerType | False | The page size to use for the endpoint. |
| pageToken | stringType | False | The page token indicates where to start paging. This should be omitted from the first page's request. To fetch the next page, clients should take the value from the `nextPageToken` field of the previous response and use it to populate the `pageToken` field of the next request. |

### Response

#### Body

**name:** ListChildrenOfFolderResponse

**example:** {"data":[{"projectRid":"ri.compass.main.folder.4cae7c13-b59f-48f6-9ef2-dbde603e4e33","updatedTime":"2024-09-25T17:29:35.974Z","updatedBy":"f05f8da4-b84c-4fca-9c77-8af0b13d11de","displayName":"My Dataset","description":"This dataset contains important data about Empyrean Airlines","rid":"ri.foundry.main.dataset.c26f11c8-cdb3-4f44-9f5d-9816ea1c82da","type":"FOUNDRY_DATASET","spaceRid":"ri.compass.main.folder.a86ad5f5-3db5-48e4-9fdd-00aa3e5731ca","trashStatus":"NOT_TRASHED","parentFolderRid":"ri.compass.main.folder.4cae7c13-b59f-48f6-9ef2-dbde603e4e33","path":"/Empyrean Airlines/My Important Project/My Dataset","createdBy":"f05f8da4-b84c-4fca-9c77-8af0b13d11de","createdTime":"2024-09-25T17:29:35.974Z"}],"nextPageToken":"v1.QnVpbGQgdGhlIEZ1dHVyZTogaHR0cHM6Ly93d3cucGFsYW50aXIuY29tL2NhcmVlcnMvP2xldmVyLXNvdXJjZSU1YiU1ZD1BUElEb2NzI29wZW4tcG9zaXRpb25z"}

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| data | listType | False |  |
| nextPageToken | stringType | False | The page token indicates where to start paging. This should be omitted from the first page's request. To fetch the next page, clients should take the value from the `nextPageToken` field of the previous response and use it to populate the `pageToken` field of the next request. |

**example:** {"data":[{"projectRid":"ri.compass.main.folder.4cae7c13-b59f-48f6-9ef2-dbde603e4e33","updatedTime":"2024-09-25T17:29:35.974Z","updatedBy":"f05f8da4-b84c-4fca-9c77-8af0b13d11de","displayName":"My Dataset","description":"This dataset contains important data about Empyrean Airlines","rid":"ri.foundry.main.dataset.c26f11c8-cdb3-4f44-9f5d-9816ea1c82da","type":"FOUNDRY_DATASET","spaceRid":"ri.compass.main.folder.a86ad5f5-3db5-48e4-9fdd-00aa3e5731ca","trashStatus":"NOT_TRASHED","parentFolderRid":"ri.compass.main.folder.4cae7c13-b59f-48f6-9ef2-dbde603e4e33","path":"/Empyrean Airlines/My Important Project/My Dataset","createdBy":"f05f8da4-b84c-4fca-9c77-8af0b13d11de","createdTime":"2024-09-25T17:29:35.974Z"}],"nextPageToken":"v1.QnVpbGQgdGhlIEZ1dHVyZTogaHR0cHM6Ly93d3cucGFsYW50aXIuY29tL2NhcmVlcnMvP2xldmVyLXNvdXJjZSU1YiU1ZD1BUElEb2NzI29wZW4tcG9zaXRpb25z"}

### Error Responses

| name | description |
| --- | --- |
| InvalidFolder | The given Resource is not a Folder. |
| GetRootFolderNotSupported | Getting the root folder as a resource is not supported. |
| GetSpaceResourceNotSupported | Getting a space as a resource is not supported. |
| FolderNotFound | The given Folder could not be found. |
| ResourceNotFound | The given Resource could not be found. |
