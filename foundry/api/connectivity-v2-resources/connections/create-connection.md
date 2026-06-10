---
source_url: "https://www.palantir.com/docs/foundry/api/connectivity-v2-resources/connections/create-connection/"
title: "Create Connection \u2022 API Reference"
---
# Create Connection

## Endpoint

Creates a new Connection with a [direct connection](/docs/foundry/data-connection/core-concepts/#direct-connection) runtime.

Any secrets specified in the request body are transmitted over the network encrypted using TLS. Once the
secrets reach Foundry's servers, they will be temporarily decrypted and remain in plaintext in memory to
be processed as needed. They will stay in plaintext in memory until the garbage collection process cleans
up the memory. The secrets are always stored encrypted on our servers.
By using this endpoint, you acknowledge and accept any potential risks associated with the temporary
in-memory handling of secrets. If you do not want your secrets to be temporarily decrypted, you should
use the Foundry UI instead.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:connectivity-connection-write`.

**operationId:** v2.createConnection

**path:** /api/v2/connectivity/connections

### Operation Type

### Scopes

| name |
| --- |
| api:connectivity-connection-write |

### Request

#### Body

**name:** CreateConnectionRequest

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| parentFolderRid | stringType | True | The unique resource identifier (RID) of a Folder. |
| configuration | unionType | True |  |
| displayName | stringType | True | The display name of the Connection. The display name must not be blank. |
| worker | unionType | True | [The worker of a Connection](/docs/foundry/data-connection/core-concepts/#workers), which defines where compute for capabilities are run. |

**example:** {"parentFolderRid":"ri.compass.main.folder.c410f510-2937-420e-8ea3-8c9bcb3c1791","configuration":{"type":"jdbc","url":"jdbc:postgresql://localhost:5432/test","driverClass":"org.postgresql.Driver"},"displayName":"Connection to my external system"}

### Response

#### Body

The created Connection

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
| ConnectionTypeNotSupported | The specified connection is not yet supported in the Platform API. |
| PropertyCannotBeBlank | The specified property cannot be blank. |
| ParentFolderNotFoundForConnection | The parent folder for the specified connection could not be found. |
| UnknownWorkerCannotBeUsedForCreatingOrUpdatingConnections | The UnknownWorker cannot be used for creating or updating connections. Please use the Foundry worker instead. |
| CreateConnectionPermissionDenied | Could not create the Connection. |
| FolderNotFound | The given Folder could not be found. |
| ConnectionNotFound | The given Connection could not be found. |
