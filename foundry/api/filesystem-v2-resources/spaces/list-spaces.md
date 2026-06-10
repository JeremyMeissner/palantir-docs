---
source_url: "https://www.palantir.com/docs/foundry/api/filesystem-v2-resources/spaces/list-spaces/"
title: "List Spaces \u2022 API Reference"
---
# List Spaces

## Endpoint

Lists all Spaces.

This is a paged endpoint. Each page may be smaller or larger than the requested page size. However, it is guaranteed that if there are more results available, the `nextPageToken` field will be populated. To get the next page, make the same request again, but set the value of the `pageToken` query parameter to be value of the `nextPageToken` value of the previous response. If there is no `nextPageToken` field in the response, you are on the last page.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:filesystem-read`.

**operationId:** v2.listSpaces

**path:** /api/v2/filesystem/spaces

### Operation Type

### Scopes

| name |
| --- |
| api:filesystem-read |

### Query Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| pageSize | integerType | False | The page size to use for the endpoint. |
| pageToken | stringType | False | The page token indicates where to start paging. This should be omitted from the first page's request. To fetch the next page, clients should take the value from the `nextPageToken` field of the previous response and use it to populate the `pageToken` field of the next request. |

### Response

#### Body

**name:** ListSpacesResponse

**example:** {"data":[{"path":"/My space-576e4","usageAccountRid":"ri.resource-policy-manager.global.usage-account.0c91194d-b5e3-4c4f-b96f-7a7f3f50e95c","fileSystemId":"hdfs","displayName":"My Space","organizations":["ri.multipass..organization.c30ee6ad-b5e4-4afe-a74f-fe4a289f2faa"],"description":"This space is for xyz","deletionPolicyOrganizations":["ri.multipass..organization.c30ee6ad-b5e4-4afe-a74f-fe4a289f2faa"],"defaultRoleSetId":"3181190f-f6b8-4649-90ec-64fa2d847204","spaceMavenIdentifier":"com.palantir.your-space","rid":"ri.compass.main.folder.c410f510-2937-420e-8ea3-8c9bcb3c1791"}],"nextPageToken":"v1.QnVpbGQgdGhlIEZ1dHVyZTogaHR0cHM6Ly93d3cucGFsYW50aXIuY29tL2NhcmVlcnMvP2xldmVyLXNvdXJjZSU1YiU1ZD1BUElEb2NzI29wZW4tcG9zaXRpb25z"}

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| data | listType | False |  |
| nextPageToken | stringType | False | The page token indicates where to start paging. This should be omitted from the first page's request. To fetch the next page, clients should take the value from the `nextPageToken` field of the previous response and use it to populate the `pageToken` field of the next request. |

**example:** {"data":[{"path":"/My space-576e4","usageAccountRid":"ri.resource-policy-manager.global.usage-account.0c91194d-b5e3-4c4f-b96f-7a7f3f50e95c","fileSystemId":"hdfs","displayName":"My Space","organizations":["ri.multipass..organization.c30ee6ad-b5e4-4afe-a74f-fe4a289f2faa"],"description":"This space is for xyz","deletionPolicyOrganizations":["ri.multipass..organization.c30ee6ad-b5e4-4afe-a74f-fe4a289f2faa"],"defaultRoleSetId":"3181190f-f6b8-4649-90ec-64fa2d847204","spaceMavenIdentifier":"com.palantir.your-space","rid":"ri.compass.main.folder.c410f510-2937-420e-8ea3-8c9bcb3c1791"}],"nextPageToken":"v1.QnVpbGQgdGhlIEZ1dHVyZTogaHR0cHM6Ly93d3cucGFsYW50aXIuY29tL2NhcmVlcnMvP2xldmVyLXNvdXJjZSU1YiU1ZD1BUElEb2NzI29wZW4tcG9zaXRpb25z"}
