---
source_url: "https://www.palantir.com/docs/foundry/api/connectivity-v2-resources/connections/get-connection/"
title: "Get Connection \u2022 API Reference"
---
# Get Connection

## Endpoint

Get the Connection with the specified rid.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:connectivity-connection-read`.

**operationId:** v2.getConnection

**path:** /api/v2/connectivity/connections/{connectionRid}

### Operation Type

### Scopes

| name |
| --- |
| api:connectivity-connection-read |

### Path Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| connectionRid | stringType | True | The Resource Identifier (RID) of a Connection (also known as a source). |

### Response

#### Body

**name:** Connection

**example:** {"parentFolderRid":"ri.compass.main.folder.c410f510-2937-420e-8ea3-8c9bcb3c1791","configuration":{"type":"jdbc","url":"jdbc:postgresql://localhost:5432/test","driverClass":"org.postgresql.Driver"},"displayName":"Connection to my external system","exportSettings":{"exportsEnabled":true,"exportEnabledWithoutMarkingsValidation":false},"rid":"ri.magritte..source.c078b71b-92f9-41b6-b0df-3760f411120b"}

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| rid | stringType | True | The Resource Identifier (RID) of a Connection (also known as a source). |
| parentFolderRid | stringType | True | The unique resource identifier (RID) of a Folder. |
| displayName | stringType | True | The display name of the Connection. The display name must not be blank. |
| exportSettings | objectType | True | The [export settings of a Connection](/docs/foundry/data-connection/export-overview/#enable-exports-for-source). |
| worker | unionType | True | [The worker of a Connection](/docs/foundry/data-connection/core-concepts/#workers), which defines where compute for capabilities are run. |
| configuration | unionType | True |  |

**example:** {"parentFolderRid":"ri.compass.main.folder.c410f510-2937-420e-8ea3-8c9bcb3c1791","configuration":{"type":"jdbc","url":"jdbc:postgresql://localhost:5432/test","driverClass":"org.postgresql.Driver"},"displayName":"Connection to my external system","exportSettings":{"exportsEnabled":true,"exportEnabledWithoutMarkingsValidation":false},"rid":"ri.magritte..source.c078b71b-92f9-41b6-b0df-3760f411120b"}

### Error Responses

| name | description |
| --- | --- |
| ParentFolderNotFoundForConnection | The parent folder for the specified connection could not be found. |
| ConnectionTypeNotSupported | The specified connection is not yet supported in the Platform API. |
| ConnectionNotFound | The given Connection could not be found. |
