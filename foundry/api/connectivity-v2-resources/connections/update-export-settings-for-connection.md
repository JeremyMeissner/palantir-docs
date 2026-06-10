---
source_url: "https://www.palantir.com/docs/foundry/api/connectivity-v2-resources/connections/update-export-settings-for-connection/"
title: "Update Export Settings For Connection \u2022 API Reference"
---
# Update Export Settings For Connection

## Endpoint

Updates the [export settings on the Connection.](/docs/foundry/data-connection/export-overview/#enable-exports-for-source)
Only users with Information Security Officer role can modify the export settings.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:connectivity-connection-write`.

**operationId:** v2.updateExportSettingsForConnection

**path:** /api/v2/connectivity/connections/{connectionRid}/updateExportSettings

### Operation Type

### Scopes

| name |
| --- |
| api:connectivity-connection-write |

### Path Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| connectionRid | stringType | True | The Resource Identifier (RID) of a Connection (also known as a source). |

### Request

#### Body

**name:** UpdateExportSettingsForConnectionRequest

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| exportSettings | objectType | True | The [export settings of a Connection](/docs/foundry/data-connection/export-overview/#enable-exports-for-source). |

**example:** {"exportSettings":{"exportsEnabled":true,"exportEnabledWithoutMarkingsValidation":false}}

### Error Responses

| name | description |
| --- | --- |
| UpdateExportSettingsForConnectionPermissionDenied | Could not updateExportSettings the Connection. |
| ConnectionNotFound | The given Connection could not be found. |
